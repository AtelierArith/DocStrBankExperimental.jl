```
compact_token_formatter(tokens::TokenCounts, cost::Float64, elapsed::Union{Float64,Nothing}=nothing)
```

トークン統計をコンパクトで絵文字装飾された形式でフォーマットします: `[🔤 in:X out:Y cache:(w:Z,r:W) 💰$C ⚡️Ts]`
