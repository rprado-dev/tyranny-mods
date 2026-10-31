# tyranny mods

The mod list for the tyranny Project Zomboid server (Build 42, first person through Project Viewpoint).

`mods.json` is the single source of truth. Two things read it:

- **The server** reads it before every start and writes the `WorkshopItems=` and `Mods=` lines of its ini.
- **Tyranny Mod Updater**, the players' setup app, downloads it from the raw URL each time a player presses **Update**, then subscribes them to every listed Workshop item:

  ```
  https://raw.githubusercontent.com/rprado-dev/tyranny-mods/main/mods.json
  ```

## Changing the mods

Edit `mods.json`, commit, and push to `main`. Players get the new list the next time they press **Update** (GitHub can take a few minutes to serve the new version), and the server picks it up on its next start.

Order matters: `mods` is the server's load order. Keep ZombieBuddy first, then Viewpoint and its add-ons, then `NeatUI_Framework` before the Neat mods.

## Fields

| Field | Meaning |
|---|---|
| `server` | Display name shown in the app. |
| `gameBuild` | Game build the list targets (informational). |
| `branch` | Optional Steam branch the server runs; empty or missing means the public branch. The app warns players on a different branch. |
| `gameRamGB` | Default position of the app's game memory slider (8 to 16 GB). |
| `mods[].workshop` | Steam Workshop item ID. |
| `mods[].id` | Mod ID from the item's `mod.info`; what goes in the server's `Mods=` line. |
| `mods[].name` | Name shown to players in the app. |
