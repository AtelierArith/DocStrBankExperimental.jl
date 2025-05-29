```
autocor(x, [lags]; demean=true)
```

Compute the autocorrelation function (ACF) of a vector or matrix `x`, optionally specifying the `lags`. `demean` denotes whether the mean of `x` should be subtracted from `x` before computing the ACF.

If `x` is a vector, return a vector of the same length as `lags`. If `x` is a matrix, return a matrix of size `(length(lags), size(x,2))`, where each column in the result corresponds to a column in `x`.

When left unspecified, the lags used are the integers from 0 to `min(size(x,1)-1, 10*log10(size(x,1)))`.

The output is normalized by the variance of `x`, i.e. so that the lag 0 autocorrelation is 1. See [`autocov`](@ref) for the unnormalized form.
