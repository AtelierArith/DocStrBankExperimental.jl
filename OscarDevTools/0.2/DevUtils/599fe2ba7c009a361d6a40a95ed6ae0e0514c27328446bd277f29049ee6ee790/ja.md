```
oscar_update(; <キーワード引数>)
```

各Oscarパッケージの`dir`内で、すべてのリモートを取得し、現在追跡中のアップストリームブランチとファストフォワードマージを行います。各ディレクトリで`git pull --ff-only`を実行するのに似ています。

# 引数

  * `dir="oscar-dev"`: 開発サブディレクトリ。
