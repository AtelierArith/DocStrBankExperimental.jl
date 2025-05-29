```
set_upper_bound(v::VariableRef, upper::Number)
```

Set the upper bound of a variable. If one does not exist, create an upper bound constraint.

See also [`UpperBoundRef`](@ref), [`has_upper_bound`](@ref), [`upper_bound`](@ref), [`delete_upper_bound`](@ref).
