```
credit_card_cvv(n::Integer = 1; kwargs...)
```

Generate `n` credit card ccvs, e.g. `034`

# Examples

```@repl
julia> credit_card_cvv(3)
3-element Vector{Int64}:
 636
 429
 117

```
