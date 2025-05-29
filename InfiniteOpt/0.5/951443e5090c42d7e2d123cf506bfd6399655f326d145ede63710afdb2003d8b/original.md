```
set_supports(pref::IndependentParameterRef, supports::Vector{<:Real};
             [force::Bool = false,
             label::Type{<:AbstractSupportLabel} = UserDefined]
             )::Nothing
```

Specify the support points for `pref`. Errors if the supports violate the bounds associated with the infinite domain. Warns if the points are not unique. If `force` this will overwrite exisiting supports otherwise it will error if there are existing supports.

**Example**

```julia-repl
julia> set_supports(t, [0, 1])

julia> supports(t)
2-element Array{Int64,1}:
 0
 1
```
