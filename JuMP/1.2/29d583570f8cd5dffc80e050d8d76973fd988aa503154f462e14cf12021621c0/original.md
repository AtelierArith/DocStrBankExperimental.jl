```
start_value(con_ref::ConstraintRef)
```

Return the primal start value ([`MOI.ConstraintPrimalStart`](@ref)) of the constraint `con_ref`.

Note: If no primal start value has been set, `start_value` will return `nothing`.

See also [`set_start_value`](@ref).
