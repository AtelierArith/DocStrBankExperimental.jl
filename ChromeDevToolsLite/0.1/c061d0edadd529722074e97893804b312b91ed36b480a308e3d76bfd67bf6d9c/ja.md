```
content(client::WSClient; verbose::Bool=false) -> String
```

現在のページのHTMLコンテンツを取得します。

# 引数

  * `client::WSClient`: 使用するWebSocketクライアント
  * `verbose::Bool`: 詳細ログを有効にする（デフォルト: false）

# 戻り値

  * `String`: ページのHTMLコンテンツ
