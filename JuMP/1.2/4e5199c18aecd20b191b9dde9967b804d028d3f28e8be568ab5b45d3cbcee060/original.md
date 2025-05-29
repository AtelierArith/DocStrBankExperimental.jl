```
has_lower_bound(v::VariableRef)
```

Return `true` if `v` has a lower bound. If `true`, the lower bound can be queried with [`lower_bound`](@ref).

See also [`LowerBoundRef`](@ref), [`lower_bound`](@ref), [`set_lower_bound`](@ref), [`delete_lower_bound`](@ref).
