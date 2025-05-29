```
Jtv = jtprod_residual!(nls, rows, cols, vals, v, Jtv)
```

Computes the product of the transpose of the Jacobian of the residual given by `(rows, cols, vals)` and a vector, i.e.,  $J(x)^Tv$, storing it in `Jv`.
