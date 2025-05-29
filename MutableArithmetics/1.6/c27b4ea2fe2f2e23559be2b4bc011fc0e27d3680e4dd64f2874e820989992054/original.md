```
rewrite_and_return(
    expr;
    move_factors_into_sums::Bool = true,
    return_is_mutable::Bool = false,
) -> Expr
```

Rewrite the expression `expr` using mutable arithmetics and return an expression in which the last statement is equivalent to `expr`.

See [`rewrite`](@ref) for an explanation of the keyword arguments.
