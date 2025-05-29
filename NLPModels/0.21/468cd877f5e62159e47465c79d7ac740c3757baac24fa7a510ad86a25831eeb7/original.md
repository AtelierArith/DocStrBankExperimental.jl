```
H = hess_residual(nls, x, v)
```

Computes the linear combination of the Hessians of the residuals at `x` with coefficients `v`. A `Symmetric` object wrapping the lower triangle is returned.
