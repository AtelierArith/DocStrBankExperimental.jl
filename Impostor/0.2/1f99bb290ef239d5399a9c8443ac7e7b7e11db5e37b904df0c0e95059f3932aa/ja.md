```
credit_card_cvv(n::Integer = 1; kwargs...)
```

`n` 個のクレジットカード CVV を生成します。例: `034`

# 例

```@repl
julia> credit_card_cvv(3)
3-element Vector{Int64}:
 636
 429
 117

```
