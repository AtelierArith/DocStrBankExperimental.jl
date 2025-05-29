```
rewrite(
    expr;
    move_factors_into_sums::Bool = true,
    return_is_mutable::Bool = false,
) -> Tuple{Symbol,Expr[,Bool]}
```

Rewrites the expression `expr` to use mutable arithmetics.

Returns `(variable, code)` comprised of a `gensym`'d variable equivalent to `expr` and the code necessary to create the variable.

## `move_factors_into_sums`

If `move_factors_into_sums = true`, some terms are rewritten based on the assumption that summations produce a linear function.

For example, if `move_factors_into_sums = true`, then `y * sum(x[i] for i in 1:2)` is rewritten to:

```julia
variable = MA.Zero()
for i in 1:2
    variable = MA.operate!!(MA.add_mul, result, y, x[i])
end
```

If `move_factors_into_sums = false`, it is rewritten to:

```julia
term = MA.Zero()
for i in 1:2
    term = MA.operate!!(MA.add_mul, term, x[i])
end
variable = MA.operate!!(*, y, term)
```

The latter can produce an additional allocation if there is an efficient fallback for `add_mul` and not for `*(y, term)`.

## `return_is_mutable`

If `return_is_mutable = true`, this function returns three arguments. The third is a `Bool` indicating if the returned expression can be safely mutated without changing the user's original expression.

`return_is_mutable` cannot be `true` if `move_factors_into_sums = true`.
