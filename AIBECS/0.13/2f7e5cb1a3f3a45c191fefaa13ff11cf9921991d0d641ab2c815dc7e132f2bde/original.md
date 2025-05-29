```
smooth_operator(grd, T; σs=(1.0, 1.0, 0.25))
```

return a matrix of the same size and sparsity as `T` that smoothes data using a Gaussian Kernel for values, but conserving mass.

This matrix can also likely be used as a covariance matrix for observations in a Bayesian framework.
