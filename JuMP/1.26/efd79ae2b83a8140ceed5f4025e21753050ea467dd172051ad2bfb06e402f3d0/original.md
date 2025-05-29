```
set_objective(model::AbstractModel, sense::MOI.OptimizationSense, func)
```

The functional equivalent of the [`@objective`](@ref) macro.

This function sets the objective sense and objective function simultaneously, and it is equivalent to calling [`set_objective_sense`](@ref) followed by [`set_objective_function`](@ref).

This is a low-level function; the recommended way to set the objective function and sense is with the [`@objective`](@ref) macro.

## FEASIBILITY_SENSE

You should not set `sense` to [`FEASIBILITY_SENSE`](@ref) because [`FEASIBILITY_SENSE`](@ref) implies that there is no objective function.

Instead of `set_objective(model, FEASIBILITY_SENSE, f)`, do `set_objective_sense(model, FEASIBILITY_SENSE)`.

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> set_objective(model, MIN_SENSE, x)

julia> objective_sense(model)
MIN_SENSE::OptimizationSense = 0

julia> objective_function(model)
x
```
