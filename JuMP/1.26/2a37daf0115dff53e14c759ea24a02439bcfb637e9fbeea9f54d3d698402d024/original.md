```
objective_sense(model::GenericModel)::MOI.OptimizationSense
```

Return the objective sense.

This function is equivalent to querying the [`MOI.ObjectiveSense`](@ref) attribute.

## Example

```jldoctest
julia> model = Model();

julia> objective_sense(model)
FEASIBILITY_SENSE::OptimizationSense = 2

julia> @variable(model, x);

julia> @objective(model, Max, x)
x

julia> objective_sense(model)
MAX_SENSE::OptimizationSense = 1
```
