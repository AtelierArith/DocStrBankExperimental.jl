```
download_scene(scene, dir=pwd(); unzip=false, log_progress=true, access_token=nothing)
```

要求されたSentinelシーンを提供されたアクセストークンを使用してダウンロードします。

# パラメータ

  * `scene`: ダウンロードするjentinelシーンの名前。
  * `dir`: ダウンロードしたシーンの保存先ディレクトリ（デフォルト = pwd()）。

# キーワード

  * `unzip`: trueの場合、ダウンロードしたzipファイルを解凍して削除します（デフォルト = false）。
  * `log_progress`: trueの場合、1秒ごとにダウンロードの進捗をログに記録します（デフォルト = true）。
  * `access_token`: リクエストを認証するためのトークン。`nothing`の場合は`get_access_token()`を呼び出します（デフォルト）。
