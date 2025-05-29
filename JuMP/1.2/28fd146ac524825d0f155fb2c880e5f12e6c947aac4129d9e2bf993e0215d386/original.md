```
dual_start_value(con_ref::ConstraintRef)
```

Return the dual start value (MOI attribute `ConstraintDualStart`) of the constraint `con_ref`.

Note: If no dual start value has been set, `dual_start_value` will return `nothing`.

See also [`set_dual_start_value`](@ref).
