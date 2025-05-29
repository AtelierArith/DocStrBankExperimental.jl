```
add_supports(prefs::AbstractArray{<:DependentParameterRef},
             supports::Vector{<:AbstractArray{<:Real}};
             [label::Type{<:AbstractSupportLabel} = UserDefined])::Nothing
```

Add additional support points for `prefs`. Errors if the supports violate the domain of the infinite domain, if the dimensions don't match up properly, if `prefs` and `supports` have different indices, or not all of the `prefs` are from the same dependent infinite parameter container.

```julia
    add_supports(prefs::Vector{DependentParameterRef},
                 supports::Array{<:Real, 2};
                 [label::Type{<:AbstractSupportLabel} = UserDefined])::Nothing
```

Specify the supports for a vector `prefs` of dependent infinite parameters. Here rows of `supports` correspond to `prefs` and the columns correspond to the supports. This is more efficient than the above method and will error for the same reasons.

**Example**

```julia-repl
julia> add_supports(x, [[1], [1]])

julia> supports(x)
2×2 Array{Float64,2}:
 0.0  1.0
 0.0  1.0

julia> add_supports(x, ones(2, 1) * 0.5)

julia> supports(t)
2×3 Array{Float64,2}:
 0.0  1.0  0.5
 0.0  1.0  0.5
```
