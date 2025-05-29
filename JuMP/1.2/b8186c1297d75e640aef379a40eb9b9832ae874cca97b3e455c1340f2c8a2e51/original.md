```
is_fixed(v::VariableRef)
```

Return `true` if `v` is a fixed variable. If `true`, the fixed value can be queried with [`fix_value`](@ref).

See also [`FixRef`](@ref), [`fix_value`](@ref), [`fix`](@ref), [`unfix`](@ref).
