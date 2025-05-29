```
evaluate(B::AbstractBSplineBasis, i::Integer, x,
         [op::AbstractDifferentialOp], [T=Float64])
```

Evaluate $i$-th basis function in the given basis at `x` (can be a coordinate or a vector of coordinates).

To evaluate a derivative, pass `Derivative(n)` as the `op` argument, with `n` the derivative order.

More general differential operators, such as `Derivative(n) + λ Derivative(m)`, are also supported.

See also [`evaluate!`](@ref).
