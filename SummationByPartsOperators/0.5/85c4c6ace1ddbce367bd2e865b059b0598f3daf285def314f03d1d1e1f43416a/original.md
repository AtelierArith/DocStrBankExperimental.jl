```
mul_transpose_derivative_left!(u, D::DerivativeOperator, der_order::Val{N}, α=true, β=false)
```

Set the grid function `u` to `α` times the transposed `N`-th derivative functional applied to `u` plus `β` times `u` in the domain of the `N`-th derivative functional at the left boundary of the grid. Thus, the coefficients `α, β` have the same meaning as in [`mul!`](@ref).
