```
get_cities(countrycode::String,statecode::String)::Dict{Int,String}
```

**Summary**: `get_cities` returns a Dict of Cities by countrycode and statecode, key is city code, value is city name.

# Arguments

  * `countrycode`: Country code to be queried.
  * `statecode`: State code to be queried.

# Example

```julia-repl
julia> get_cities("CN","01")
cites = Dict(10398 => "Wucheng"...)
```
