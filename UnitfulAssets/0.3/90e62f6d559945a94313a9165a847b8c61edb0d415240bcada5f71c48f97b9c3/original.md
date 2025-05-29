```
generate_exchmkt(d::Dict{Tuple{String,String},T}) where {T<:Number}
```

Generate an instance of `ExchangeMarket` from a dictionary of base-quote-value rates.

# Examples

```jldoctest
julia> generate_exchmkt(Dict(("EUR", "USD") => 1.164151))
Dict{AssetsPair,Float64} with 1 entry:
  AssetsPair("EUR", "USD") => Rate(1.16415)
```
