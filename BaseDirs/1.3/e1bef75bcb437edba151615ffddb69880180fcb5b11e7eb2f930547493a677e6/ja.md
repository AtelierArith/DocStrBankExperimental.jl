**BIN_HOME** (`XDG_BIN_HOME`)

ユーザー固有の実行可能ファイルが書き込まれるべき単一のベースディレクトリ。

**デフォルト値**

|          Linux |           MacOS* |             Windows* |
| --------------:| ----------------:| --------------------:|
| `~/.local/bin` |   `~/.local/bin` |               `\bin` |
|                | `/opt/local/bin` | `RoamingAppData\bin` |
|                | `/usr/local/bin` |        `AppData\bin` |
|                |                  |          現在の作業ディレクトリ |

  * 存在する最初のディレクトリが使用されます。

!!! warning
    これはまだXDGによって標準化されていません。詳細については、[freedesktop.org/xdg-specs#14](https://gitlab.freedesktop.org/xdg/xdg-specs/-/issues/14)を参照してください。

