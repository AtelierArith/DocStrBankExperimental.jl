```
set_nonlinear_objective(
    model::Model,
    sense::MOI.OptimizationSense,
    expr::Expr,
)
```

Set the nonlinear objective of `model` to the expression `expr`, with the optimization sense `sense`.

This function is most useful if the expression `expr` is generated programmatically, and you cannot use [`@NLobjective`](@ref).

## Notes

  * You must interpolate the variables directly into the expression `expr`.
  * You must use `MIN_SENSE` or `MAX_SENSE` instead of `Min` and `Max`.

## Examples

```jldoctest; setup=:(using JuMP; model = Model(); @variable(model, x))
julia> set_nonlinear_objective(model, MIN_SENSE, :($(x) + $(x)^2))
```
