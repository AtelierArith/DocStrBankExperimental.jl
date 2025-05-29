```
FixRef(v::VariableRef)
```

Return a constraint reference to the constraint fixing the value of `v`. Errors if one does not exist.

See also [`is_fixed`](@ref), [`fix_value`](@ref), [`fix`](@ref), [`unfix`](@ref).
