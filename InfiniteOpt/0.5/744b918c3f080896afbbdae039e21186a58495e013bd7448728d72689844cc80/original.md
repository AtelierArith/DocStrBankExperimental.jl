```
JuMP.objective_sense(model::InfiniteModel)::MOI.OptimizationSense
```

Extend `JuMP.objective_sense` to return the objective sense of the infinite model  `model`.

**Example**

```julia-repl
julia> objective_sense(model)
MIN_SENSE::OptimizationSense = 0
```
