```
Jx = jac_op_residual!(nls, x, Jv, Jtv)
```

Computes $J(x)$, the Jacobian of the residual at x, in linear operator form. The vectors `Jv` and `Jtv` are used as preallocated storage for the operations.
