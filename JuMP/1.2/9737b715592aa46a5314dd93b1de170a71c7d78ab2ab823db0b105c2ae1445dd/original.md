```
@NLexpressions(model, args...)
```

Adds multiple nonlinear expressions to model at once, in the same fashion as the [`@NLexpression`](@ref) macro.

The model must be the first argument, and multiple expressions can be added on multiple lines wrapped in a `begin ... end` block.

The macro returns a tuple containing the expressions that were defined.

# Examples

```julia
@NLexpressions(model, begin
    my_expr, sqrt(x^2 + y^2)
    my_expr_1[i = 1:2], log(a[i]) - z[i]
end)
```
