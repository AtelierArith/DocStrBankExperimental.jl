```
screenshot(client::WSClient; verbose::Bool=false) -> String
```

現在のページのスクリーンショットを撮ります。

# 引数

  * `client::WSClient`: 使用するWebSocketクライアント
  * `save_path::String`: スクリーンショットファイルを保存するパス（デフォルト: 空文字列）。空でない場合、指定されたパスにスクリーンショットが保存されます。
  * `verbose::Bool`: 詳細ログを有効にする（デフォルト: false）

# 戻り値

  * `String`: スクリーンショットのBase64エンコードされた文字列、またはキャプチャに失敗した場合は何も返さない
