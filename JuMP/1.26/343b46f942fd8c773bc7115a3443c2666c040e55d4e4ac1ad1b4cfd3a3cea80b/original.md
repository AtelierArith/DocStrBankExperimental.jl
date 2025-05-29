```
set_objective_sense(model::GenericModel, sense::MOI.OptimizationSense)
```

Sets the objective sense of the model to the given sense.

See also: [`@objective`](@ref), [`set_objective_function`](@ref), [`set_objective`](@ref)

## FEASIBILITY_SENSE

Setting the objective sense to [`FEASIBILITY_SENSE`](@ref) will remove any existing objective.

## Example

```jldoctest
julia> model = Model();

julia> objective_sense(model)
FEASIBILITY_SENSE::OptimizationSense = 2

julia> set_objective_sense(model, MOI.MAX_SENSE)

julia> objective_sense(model)
MAX_SENSE::OptimizationSense = 1
```
