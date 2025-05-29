```
H = hess_op!(nlp, x, y, Hv; obj_weight=1.0)
```

Return the Lagrangian Hessian at `(x,y)` with objective function scaled by `obj_weight` as a linear operator, and storing the result on `Hv`. The resulting object may be used as if it were a matrix, e.g., `w = H * v`. The vector `Hv` is used as preallocated storage for the operation.  The linear operator H represents

$$
∇²L(x,y) = σ ∇²f(x) + \sum_i yᵢ ∇²cᵢ(x),
$$

with `σ = obj_weight` .
