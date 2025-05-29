```
set_start_value(con_ref::ConstraintRef, value)
```

Set the primal start value ([`MOI.ConstraintPrimalStart`](@ref)) of the constraint `con_ref` to `value`. To remove a primal start value set it to `nothing`.

See also [`start_value`](@ref).
