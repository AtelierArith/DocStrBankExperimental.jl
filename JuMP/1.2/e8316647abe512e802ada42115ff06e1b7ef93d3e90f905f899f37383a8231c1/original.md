```
set_objective(model::AbstractModel, sense::MOI.OptimizationSense, func)
```

The functional equivalent of the [`@objective`](@ref) macro.

Sets the objective sense and objective function simultaneously, and is equivalent to:

```julia
set_objective_sense(model, sense)
set_objective_function(model, func)
```

## Examples

```jldoctest; setup=:(using JuMP)
model = Model()
@variable(model, x)
set_objective(model, MIN_SENSE, x)
```
