```
H = hess_op!(nlp, rows, cols, vals, Hv)
```

Return the Hessian given by `(rows, cols, vals)` as a linear operator, and storing the result on `Hv`. The resulting object may be used as if it were a matrix, e.g., `w = H * v`.   The vector `Hv` is used as preallocated storage for the operation.  The linear operator H represents

$$
σ ∇²f(x),
$$

with `σ = obj_weight` .
