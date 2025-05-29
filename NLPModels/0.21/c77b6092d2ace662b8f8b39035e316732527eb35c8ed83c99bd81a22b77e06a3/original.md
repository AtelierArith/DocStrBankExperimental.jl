```
vals = hess_coord_residual!(nls, x, v, vals)
```

Computes the linear combination of the Hessians of the residuals at `x` with coefficients `v` in sparse coordinate format, rewriting `vals`.
