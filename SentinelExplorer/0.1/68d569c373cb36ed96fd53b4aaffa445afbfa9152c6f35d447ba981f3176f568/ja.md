```
download_scenes(scenes, dir=pwd(); unzip=false, access_token=nothing)
```

複数のシーンを並行してダウンロードします。

並行ダウンロードの数は `Threads.nthreads()` によって決まります。

# パラメータ

  * `scenes`: ダウンロードするシーンのリスト。

# キーワード

  * `dir`: ダウンロードしたシーンの保存先ディレクトリ（デフォルト = pwd()）。
  * `unzip`: true の場合、ダウンロードした zip ファイルを解凍して削除します（デフォルト = false）。
  * `access_token`: リクエストを認証するためのトークン。`nothing` の場合は `get_access_token()` を呼び出します（デフォルト）。
