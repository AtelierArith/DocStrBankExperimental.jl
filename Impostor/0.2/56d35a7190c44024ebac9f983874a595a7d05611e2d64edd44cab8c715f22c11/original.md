```
credit_card_expiry(n::Integer = 1; kwargs...)
```

Generate `n` credit card expiry entries, e.g. `05/2029`.

# Examples

```@repl
julia> credit_card_expiry(3)
3-element Vector{String}:
 "4/2014"
 "7/2013"
 "10/2010"
```
