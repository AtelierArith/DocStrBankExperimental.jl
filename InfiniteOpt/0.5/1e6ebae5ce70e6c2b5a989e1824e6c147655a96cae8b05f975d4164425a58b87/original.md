```
JuMP.set_objective_sense(model::InfiniteModel,
                         sense::MOI.OptimizationSense)::Nothing
```

Extend `JuMP.set_objective_sense` to set the objective sense of infinite model  `model`.

**Example**

```julia-repl
julia> set_objective_sense(model, MOI.MIN_SENSE)

julia> objective_sense(model)
MIN_SENSE::OptimizationSense = 0
```
