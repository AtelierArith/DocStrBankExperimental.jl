```
BinaryRef(v::VariableRef)
```

Return a constraint reference to the constraint constraining `v` to be binary. Errors if one does not exist.

See also [`is_binary`](@ref), [`set_binary`](@ref), [`unset_binary`](@ref).
