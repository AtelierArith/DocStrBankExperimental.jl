```
default_token_formatter(tokens::TokenCounts, cost::Float64, elapsed::Union{Float64,Nothing}=nothing)
```

Format token statistics in a default text format: `[in=X, out=Y, cache_in=Z, cache_read=W, $C, Ts]`
