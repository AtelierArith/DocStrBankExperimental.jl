```
@objective(model::GenericModel, sense, func)
```

Set the objective sense to `sense` and objective function to `func`.

## `sense`

The objective sense must be either be the literals `Min` or `Max`, or one of the three [`MOI.OptimizationSense`](@ref) enum values ([`MIN_SENSE`](@ref), [`MAX_SENSE`](@ref), or [`FEASIBILITY_SENSE`](@ref)).

In order to set the sense programmatically, that is, when `sense` is a Julia variable whose value is the sense, you must use a [`MOI.OptimizationSense`](@ref).

## FEASIBILITY_SENSE

[`FEASIBILITY_SENSE`](@ref) implies that there is no objective function. Therefore, you should not set `sense` to [`FEASIBILITY_SENSE`](@ref) with a non-zero `func`.

To reset the model to [`FEASIBILITY_SENSE`](@ref), do `@objective(model, FEASIBILITY_SENSE, 0)`, or use [`set_objective_sense`](@ref): `set_objective_sense(model, FEASIBILITY_SENSE)`.

## Example

Minimize the value of the variable `x`, do:

```jldoctest
julia> model = Model();

julia> @variable(model, x)
x

julia> @objective(model, Min, x)
x
```

Maximize the value of the affine expression `2x - 1`:

```jldoctest
julia> model = Model();

julia> @variable(model, x)
x

julia> @objective(model, Max, 2x - 1)
2 x - 1
```

Set the objective sense programmatically:

```jldoctest
julia> model = Model();

julia> @variable(model, x)
x

julia> sense = MIN_SENSE
MIN_SENSE::OptimizationSense = 0

julia> @objective(model, sense, x^2 - 2x + 1)
x² - 2 x + 1
```

Remove an objective function:

```jldoctest
julia> model = Model();

julia> @variable(model, x >= 0);

julia> @objective(model, Min, 2x + 1)
2 x + 1

julia> print(model)
Min 2 x + 1
Subject to
 x ≥ 0

julia> @objective(model, FEASIBILITY_SENSE, 0)
0

julia> print(model)
Feasibility
Subject to
 x ≥ 0
```
