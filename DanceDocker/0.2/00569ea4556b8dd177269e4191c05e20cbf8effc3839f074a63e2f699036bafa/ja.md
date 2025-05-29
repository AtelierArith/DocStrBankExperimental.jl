```
setup(path::String="."; version::String=string(VERSION))
```

  * Juliaのバージョン番号は上書き可能で、そうでなければシステムのものがデフォルトとなります
  * プロジェクトに`Project.toml`、`dance.jl`、および`settings`ディレクトリが含まれているか確認します。そうでなければ、プロジェクトはDanceJLで適切に構成されていないことを意味します
  * `Dance.Configuration.Settings`辞書から`Dockerfile`に指定されたサーバーポートを取得します
  * パッケージの`files`ディレクトリからテンプレートを使用して`Dockerfile`を生成します
