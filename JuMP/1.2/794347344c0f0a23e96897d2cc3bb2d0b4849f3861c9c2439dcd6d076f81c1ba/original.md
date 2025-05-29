```
fix(v::VariableRef, value::Number; force::Bool = false)
```

Fix a variable to a value. Update the fixing constraint if one exists, otherwise create a new one.

If the variable already has variable bounds and `force=false`, calling `fix` will throw an error. If `force=true`, existing variable bounds will be deleted, and the fixing constraint will be added. Note a variable will have no bounds after a call to [`unfix`](@ref).

See also [`FixRef`](@ref), [`is_fixed`](@ref), [`fix_value`](@ref), [`unfix`](@ref).
