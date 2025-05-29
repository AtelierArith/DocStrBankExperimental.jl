```
evaluate(client::WSClient, expression::String; verbose::Bool=false) -> Any
```

ページコンテキストでJavaScriptを評価し、結果を返します。

# 引数

  * `client::WSClient`: 使用するWebSocketクライアント
  * `expression::String`: 評価するJavaScript式
  * `verbose::Bool`: 詳細ログを有効にする（デフォルト: false）

# 戻り値

  * `Any`: JavaScript評価の結果、または値が返されない場合は何も返さない

# 例外

  * `EvaluationError`: JavaScript評価が失敗した場合
