```
Jv = jprod_residual!(nls, rows, cols, vals, v, Jv)
```

Computes the product of the Jacobian of the residual given by `(rows, cols, vals)` and a vector, i.e.,  $J(x)v$, storing it in `Jv`.
