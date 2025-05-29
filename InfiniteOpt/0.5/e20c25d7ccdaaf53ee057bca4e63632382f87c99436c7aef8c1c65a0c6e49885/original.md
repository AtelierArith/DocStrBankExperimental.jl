```
fill_in_supports!(prefs::AbstractArray{<:DependentParameterRef};
                  [num_supports::Int = DefaultNumSupports,
                   modify::Bool = true])::Nothing
```

Automatically generate support points for a container of dependent infinite parameters `prefs`. Generating up to `num_supports` for the parameters in accordance with `generate_and_add_supports!`. Will add nothing if there are supports and `modify = false`. Extensions that use user defined domain types should extend [`generate_and_add_supports!`](@ref) and/or [`generate_support_values`](@ref) as needed. Errors if the infinite domain type is not recognized.

**Example**

```julia-repl
julia> fill_in_supports!(x, num_supports = 4)

julia> supports(x)
2×4 Array{Float64,2}:
 0.0  0.333  0.667  1.0
 0.0  0.333  0.667  1.0
```
