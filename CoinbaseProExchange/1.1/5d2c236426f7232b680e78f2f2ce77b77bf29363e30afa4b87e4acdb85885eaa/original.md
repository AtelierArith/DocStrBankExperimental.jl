```
show_all_products(currency::String)
```

Fetch list of all available products for a given currency.

# Arguments

  * `currency::String` : "EUR", "USD" (default), "GBP" etc.

# Example

```julia-repl
julia> show_all_products("EUR")
40-element Vector{String}:
 "ETC-EUR"
 "SNX-EUR"
```
