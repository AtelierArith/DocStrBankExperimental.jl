```
evaluate_handle(client::WSClient, expression::String; verbose::Bool=false) -> Any
```

ページコンテキストでJavaScriptを評価し、結果へのハンドルを返します。DOM要素や複雑なオブジェクトを返す式を評価するのに便利です。

# 引数

  * `client::WSClient`: 使用するWebSocketクライアント
  * `expression::String`: 評価するJavaScript式
  * `verbose::Bool`: 詳細なログを有効にする（デフォルト: false）

# 戻り値

  * `Any`: 評価された結果へのハンドル、通常はオブジェクト参照を含むDict

# 例外

  * `EvaluationError`: JavaScriptの評価が失敗した場合
