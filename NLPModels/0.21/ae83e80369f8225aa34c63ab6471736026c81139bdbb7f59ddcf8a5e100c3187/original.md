```
H = hess_op(nlp, x; obj_weight=1.0)
```

Return the objective Hessian at `x` with objective function scaled by `obj_weight` as a linear operator. The resulting object may be used as if it were a matrix, e.g., `H * v`. The linear operator H represents

$$
σ ∇²f(x),
$$

with `σ = obj_weight` .
