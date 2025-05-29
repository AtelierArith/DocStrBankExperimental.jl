```
set_dual_start_value(con_ref::ConstraintRef, value)
```

Set the dual start value (MOI attribute `ConstraintDualStart`) of the constraint `con_ref` to `value`. To remove a dual start value set it to `nothing`.

See also [`dual_start_value`](@ref).
