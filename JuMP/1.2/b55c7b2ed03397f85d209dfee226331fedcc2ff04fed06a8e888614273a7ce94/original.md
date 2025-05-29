```
set_lower_bound(v::VariableRef, lower::Number)
```

Set the lower bound of a variable. If one does not exist, create a new lower bound constraint.

See also [`LowerBoundRef`](@ref), [`has_lower_bound`](@ref), [`lower_bound`](@ref), [`delete_lower_bound`](@ref).
