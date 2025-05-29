```
autocov!(r, x, lags; demean=true)
```

Compute the autocovariance of a vector or matrix `x` at `lags` and store the result in `r`. `demean` denotes whether the mean of `x` should be subtracted from `x` before computing the autocovariance.

If `x` is a vector, `r` must be a vector of the same length as `lags`. If `x` is a matrix, `r` must be a matrix of size `(length(lags), size(x,2))`, and where each column in the result will correspond to a column in `x`.

The output is not normalized. See [`autocor!`](@ref) for a method with normalization.
