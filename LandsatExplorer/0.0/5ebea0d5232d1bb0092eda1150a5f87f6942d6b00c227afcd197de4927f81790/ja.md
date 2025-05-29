```
download_scene(scene, dir=pwd(); log_progress=true, unpack=false)
```

Landsatシーンをダウンロードし、指定されたディレクトリに保存します。

# パラメータ

  * `scene`: ダウンロードするシーンの表示名またはエンティティID。
  * `dir`: ダウンロードしたシーンを保存するディレクトリ。

# キーワード

  * `unpack`: trueの場合、ダウンロードしたtarファイルを解凍して削除します（デフォルト = false）。
  * `log_progress`: trueの場合、1秒ごとにダウンロードの進捗をログに記録します（デフォルト = true）。

# 戻り値

ダウンロードしたファイルのパス。
