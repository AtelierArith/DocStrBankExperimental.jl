```
generate_exchmkt(a::Array{Pair{Tuple{String,String},Float64},1})
```

Generate an instance of `ExchangeMarket` from an array of base-quote-value rates.

# Examples

```jldoctest
julia> generate_exchmkt([("EUR","USD") => 1.19536, ("USD","EUR") => 0.836570])
Dict{AssetsPair,Float64} with 2 entries:
  AssetsPair("EUR", "USD") => Rate(1.19536)
  AssetsPair("USD", "EUR") => Rate(0.83657)
```
