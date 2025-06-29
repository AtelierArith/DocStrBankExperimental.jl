**STATE_HOME** (`XDG_STATE_HOME`)

The single base directory relative to which user-specific state data should be written.

This should contain  state data that should persist between (application) restarts, but that is not important or portable enough to the user that it should be stored in `DATA_HOME`. It may contain:

  * actions history (logs, history, recently used files, …)
  * current state of the application that can be reused on a restart (view, layout, open files, undo history, …)

**Default values**

|            Linux |                          MacOS |        Windows |
| ----------------:| ------------------------------:| --------------:|
| `~/.local/state` | `~/Library/ApplicationSupport` | `LocalAppData` |
