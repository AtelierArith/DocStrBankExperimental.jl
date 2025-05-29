```
get_states(countrycode::String)::Dict{String,String}
```

**Summary**: `get_states` returns a Dict of States by countrycode, key is state code, value is state name.

# Arguments

  * `countrycode`: Country code to be queried.

# Example

```julia-repl
julia> get_states("CN")
Dict("24" => "Shanxi"...)
```
