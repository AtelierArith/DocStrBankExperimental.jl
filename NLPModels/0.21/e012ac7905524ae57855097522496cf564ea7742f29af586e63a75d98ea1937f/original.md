```
Jx = jac_op_residual!(nls, rows, cols, vals, Jv, Jtv)
```

Computes $J(x)$, the Jacobian of the residual given by `(rows, cols, vals)`, in linear operator form. The vectors `Jv` and `Jtv` are used as preallocated storage for the operations.
