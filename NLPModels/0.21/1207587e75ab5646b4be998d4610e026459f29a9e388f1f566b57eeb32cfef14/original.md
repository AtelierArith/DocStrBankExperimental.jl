```
H = hess_op!(nlp, x, Hv; obj_weight=1.0)
```

Return the objective Hessian at `x` with objective function scaled by `obj_weight` as a linear operator, and storing the result on `Hv`. The resulting object may be used as if it were a matrix, e.g., `w = H * v`. The vector `Hv` is used as preallocated storage for the operation.  The linear operator H represents

$$
σ ∇²f(x),
$$

with `σ = obj_weight` .
