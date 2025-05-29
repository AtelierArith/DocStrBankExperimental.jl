**BIN_HOME** (`XDG_BIN_HOME`)

The single base directory relative to which user-specific executables should be written.

**Default values**

|          Linux |           MacOS* |             Windows* |
| --------------:| ----------------:| --------------------:|
| `~/.local/bin` |   `~/.local/bin` |               `\bin` |
|                | `/opt/local/bin` | `RoamingAppData\bin` |
|                | `/usr/local/bin` |        `AppData\bin` |
|                |                  |  current working dir |

* The first of these directories that exists is used.

!!! warning
    This is not yet standardised by the XDG, see [freedesktop.org/xdg-specs#14](https://gitlab.freedesktop.org/xdg/xdg-specs/-/issues/14) for more information.

