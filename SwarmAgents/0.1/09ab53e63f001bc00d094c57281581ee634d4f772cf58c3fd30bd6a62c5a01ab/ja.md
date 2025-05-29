```
応答
```

スワームの単一の完全ターンからの応答。

# フィールド

  * `messages::Vector{PT.AbstractMessage}`: 最後の完全ターンからの追加メッセージ。
  * `agent::Union{Agent, Nothing}`: セッション内の現在のアクティブエージェント。
  * `context::Dict{Symbol, Any}`: セッション内のコンテキスト変数またはその他のデータ。
