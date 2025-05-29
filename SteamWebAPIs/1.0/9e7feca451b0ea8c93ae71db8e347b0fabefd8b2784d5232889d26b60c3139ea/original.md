```
get_countries()::Dict{String,Tuple{Bool,String}}
```

**Summary**: `get_countries` returns a Dict of Countries,key is country code, value is a Tuple, the first element of Tuple indicates whether there has stete, the second is countryname.

# Example

```julia-repl
julia> get_countries()
countries = Dict("ES" => (1, "Spain")...)
```
