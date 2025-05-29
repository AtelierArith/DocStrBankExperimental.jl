```
set_supports(prefs::AbstractArray{<:DependentParameterRef},
             supports::Vector{<:AbstractArray{<:Real}};
             [force::Bool = false,
             label::Type{<:AbstractSupportLabel} = UserDefined])::Nothing
```

Specify the support points for `prefs`. Errors if the supports violate the domain of the infinite domain, if the dimensions don't match up properly, if `prefs` and `supports` have different indices, not all of the `prefs` are from the same dependent infinite parameter container, there are existing supports and `force = false`. Note that it is strongly preferred to use `add_supports` if possible to avoid destroying measure dependencies.

```julia
    set_supports(prefs::Vector{DependentParameterRef},
                 supports::Array{<:Real, 2};
                 [force::Bool = false,
                 label::Type{<:AbstractSupportLabel} = UserDefined])::Nothing
```

Specify the supports for a vector `prefs` of dependent infinite parameters. Here rows of `supports` correspond to `prefs` and the columns correspond to the supports. This is more efficient than the above method and will error for the same reasons.

**Example**

```julia-repl
julia> set_supports(y, [[0, 1], [0, 1]])

julia> set_supports(x, [0 1; 0 1])

julia> supports(x)
2×2 Array{Float64,2}:
 0.0  1.0
 0.0  1.0
```
