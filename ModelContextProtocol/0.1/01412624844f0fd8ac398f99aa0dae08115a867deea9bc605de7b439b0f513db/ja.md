```
MCPLogger <: AbstractLogger
```

MCPサーバー用のカスタムロガーを定義し、プロトコル要件に従ってメッセージをフォーマットします。

# フィールド

  * `stream::IO`: ログメッセージの出力ストリーム
  * `min_level::LogLevel`: 表示する最小ログレベル
  * `message_limits::Dict{Any,Int}`: レート制限のためのメッセージ制限設定
