```
add_nonlinear_expression(model::Model, expr::Expr)
```

Add a nonlinear expression `expr` to `model`.

This function is most useful if the expression `expr` is generated programmatically, and you cannot use [`@NLexpression`](@ref).

## Notes

  * You must interpolate the variables directly into the expression `expr`.

## Examples

```jldoctest; setup=:(using JuMP; model = Model(); @variable(model, x))
julia> add_nonlinear_expression(model, :($(x) + $(x)^2))
subexpression[1]: x + x ^ 2.0
```
