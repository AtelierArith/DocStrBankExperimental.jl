```
add_nonlinear_constraint(model::Model, expr::Expr)
```

Add a nonlinear constraint described by the Julia expression `ex` to `model`.

This function is most useful if the expression `ex` is generated programmatically, and you cannot use [`@NLconstraint`](@ref).

!!! compat
    This function is part of the legacy nonlinear interface. Consider using the new nonlinear interface documented in [Nonlinear Modeling](@ref).


## Notes

  * You must interpolate the variables directly into the expression `expr`.

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> add_nonlinear_constraint(model, :($(x) + $(x)^2 <= 1))
(x + x ^ 2.0) - 1.0 ≤ 0
```
