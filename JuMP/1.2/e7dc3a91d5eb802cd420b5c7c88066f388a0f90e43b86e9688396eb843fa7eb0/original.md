```
optimizer_index(cr::ConstraintRef{Model})::MOI.ConstraintIndex
```

Return the index of the constraint that corresponds to `cr` in the optimizer model. It throws [`NoOptimizer`](@ref) if no optimizer is set and throws an `ErrorException` if the optimizer is set but is not attached or if the constraint is bridged.
