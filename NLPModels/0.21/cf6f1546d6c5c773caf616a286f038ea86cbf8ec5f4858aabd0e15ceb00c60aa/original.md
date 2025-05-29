```
Hop = hess_op_residual!(nls, x, i, Hiv)
```

Computes the Hessian of the i-th residual at x, in linear operator form. The vector `Hiv` is used as preallocated storage for the operation.
