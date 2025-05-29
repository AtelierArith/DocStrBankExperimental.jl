```
differentiate(expr::Expression, var::Variable, k = 1)
differentiate(expr::AbstractVector{Expression}, var::Variable, k = 1)
```

Compute the `k`-th derivative of `expr` with respect to the given variable `var`.

```
differentiate(expr::Expression, vars::AbstractVector{Variable})
```

Compute the partial derivatives of `expr` with respect to the given variable variables `vars`. Retuns a `Vector` containing the partial derivatives.

```
differentiate(exprs::AbstractVector{Expression}, vars::AbstractVector{Variable})
```

Compute the partial derivatives of `exprs` with respect to the given variable variables `vars`. Returns a `Matrix` where the each row contains the partial derivatives for a given expression.
