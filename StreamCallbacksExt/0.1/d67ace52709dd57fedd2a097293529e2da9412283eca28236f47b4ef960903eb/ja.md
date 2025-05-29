```
default_token_formatter(tokens::TokenCounts, cost::Float64, elapsed::Union{Float64,Nothing}=nothing)
```

トークン統計をデフォルトのテキスト形式でフォーマットします: `[in=X, out=Y, cache_in=Z, cache_read=W, $C, Ts]`
