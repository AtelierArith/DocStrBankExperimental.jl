```
compute_conflict!(model::Model)
```

Compute a conflict if the model is infeasible. If an optimizer has not been set yet (see [`set_optimizer`](@ref)), a [`NoOptimizer`](@ref) error is thrown.

The status of the conflict can be checked with the `MOI.ConflictStatus` model attribute. Then, the status for each constraint can be queried with the `MOI.ConstraintConflictStatus` attribute.
