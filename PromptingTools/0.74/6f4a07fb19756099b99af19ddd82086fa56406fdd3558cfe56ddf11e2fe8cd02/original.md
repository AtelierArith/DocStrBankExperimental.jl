```
(mem::ConversationMemory)(prompt::AbstractString; last::Union{Nothing,Integer}=nothing, kwargs...)
```

Functor interface for direct generation using the conversation memory. Optionally, specify the number of last messages to include in the context (uses `get_last`).
