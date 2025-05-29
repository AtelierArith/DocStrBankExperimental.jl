```
crosscov!(r, x, y, lags; demean=true)
```

Compute the cross covariance function (CCF) between real-valued vectors or matrices `x` and `y` at `lags` and store the result in `r`. `demean` specifies whether the respective means of `x` and `y` should be subtracted from them before computing their CCF.

If both `x` and `y` are vectors, `r` must be a vector of the same length as `lags`. If either `x` is a matrix and `y` is a vector, `r` must be a matrix of size `(length(lags), size(x, 2))`; if `x` is a vector and `y` is a matrix, `r` must be a matrix of size `(length(lags), size(y, 2))`. If both `x` and `y` are matrices, `r` must be a three-dimensional array of size `(length(lags), size(x, 2), size(y, 2))`.

The output is not normalized. See [`crosscor!`](@ref) for a function with normalization.
