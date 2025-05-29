```
goto(client::WSClient, url::String; verbose::Bool=false)
```

指定されたURLに移動し、ページの読み込みを待ちます。

# 引数

  * `client::WSClient`: 使用するWebSocketクライアント
  * `url::String`: 移動するURL
  * `verbose::Bool`: 詳細なログを有効にする（デフォルト: false）

# 例外

  * `NavigationError`: ナビゲーションが失敗するか、タイムアウトした場合
