```
Session(agent::Agent;
    context::Dict{Symbol, Any} = Dict{Symbol, Any}())
```

`agent` とオプションの `context` で `Session` を初期化します。

セッションを続けるには、`user_prompt` を使って `run_full_turn!` を実行します。
