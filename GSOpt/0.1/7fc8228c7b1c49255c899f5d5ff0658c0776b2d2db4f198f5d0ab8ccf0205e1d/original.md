```
JuMP.dual(cref::GPConstraintRef) -> Float64
```

Returns the dual value (sensitivity) of the constraint.

# Arguments

  * `cref::GPConstraintRef`: The constraint reference

# Returns

  * The dual value of the constraint

# Throws

  * Error if the model has not been solved yet or if dual values are not available
