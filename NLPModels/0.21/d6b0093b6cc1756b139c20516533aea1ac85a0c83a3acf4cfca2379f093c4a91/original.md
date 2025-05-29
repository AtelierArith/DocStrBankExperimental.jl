```
H = hess_op(nlp, x, y; obj_weight=1.0)
```

Return the Lagrangian Hessian at `(x,y)` with objective function scaled by `obj_weight` as a linear operator. The resulting object may be used as if it were a matrix, e.g., `H * v`. The linear operator H represents

$$
∇²L(x,y) = σ ∇²f(x) + \sum_i yᵢ ∇²cᵢ(x),
$$

with `σ = obj_weight` .
