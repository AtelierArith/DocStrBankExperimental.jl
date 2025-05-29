```
autocov(x, [lags]; demean=true)
```

Compute the autocovariance of a vector or matrix `x`, optionally specifying the `lags` at which to compute the autocovariance. `demean` denotes whether the mean of `x` should be subtracted from `x` before computing the autocovariance.

If `x` is a vector, return a vector of the same length as `lags`. If `x` is a matrix, return a matrix of size `(length(lags), size(x,2))`, where each column in the result corresponds to a column in `x`.

When left unspecified, the lags used are the integers from 0 to `min(size(x,1)-1, 10*log10(size(x,1)))`.

The output is not normalized. See [`autocor`](@ref) for a function with normalization.
