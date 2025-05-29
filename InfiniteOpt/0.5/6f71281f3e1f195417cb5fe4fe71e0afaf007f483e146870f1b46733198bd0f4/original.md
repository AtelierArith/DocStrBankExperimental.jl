```
JuMP.set_objective(model::InfiniteModel, sense::MOI.OptimizationSense,
                   func::Union{JuMP.AbstractJuMPScalar, Real})::Nothing
```

Extend `JuMP.set_objective` to set the objective of infinite model `model`. Errors if `func` contains infinite variables and/or parameters, or if it does not belong to the model.

**Example**

```julia-repl
julia> set_objective(model, MOI.MIN_SENSE, 2x + 1)

julia> objective_function(model)
2 x + 1
```
