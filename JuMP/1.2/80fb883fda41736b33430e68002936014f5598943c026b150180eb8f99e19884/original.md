```
set_objective_sense(model::Model, sense::MOI.OptimizationSense)
```

Sets the objective sense of the model to the given sense. See [`set_objective_function`](@ref) to set the objective function. These are low-level functions; the recommended way to set the objective is with the [`@objective`](@ref) macro.
