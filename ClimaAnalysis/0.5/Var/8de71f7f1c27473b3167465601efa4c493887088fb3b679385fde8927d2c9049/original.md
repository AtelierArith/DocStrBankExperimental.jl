```
find_corresponding_dim_name(dim_name::AbstractString, dim_names::Iterable)
```

Find the corresponding dimension name in `dim_names` that matches `dim_name`.

Two names for a dimension match if both correspond to the same conventional name as determined by `Var.conventional_dim_name`.

# Example

```jldoctest
julia> ClimaAnalysis.Var.find_corresponding_dim_name("longitude", ["lat", "lon"])
"lon"

julia> ClimaAnalysis.Var.find_corresponding_dim_name("time", ["lat", "lon", "t"])
"t"

julia> ClimaAnalysis.Var.find_corresponding_dim_name("height", ["lat", "lon", "height"])
"height"
```
