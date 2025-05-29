```
(mem::ConversationMemory)(prompt::AbstractString; last::Union{Nothing,Integer}=nothing, kwargs...)
```

会話メモリを使用した直接生成のためのファンクタインターフェース。オプションで、コンテキストに含める最後のメッセージの数を指定します（`get_last`を使用）。
