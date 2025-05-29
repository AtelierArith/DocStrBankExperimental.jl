```
セッション
```

セッションは、`messages`、`agent`、および `context` を保持する可変構造体です。

# フィールド

  * `messages::Vector{PT.AbstractMessage}`: セッション内のチャットまたはツールメッセージの履歴。
  * `agent::Union{Agent, Nothing}`: セッション内の現在のアクティブエージェント。
  * `context::Dict{Symbol, Any}`: セッション内のコンテキスト変数またはその他のデータ。
