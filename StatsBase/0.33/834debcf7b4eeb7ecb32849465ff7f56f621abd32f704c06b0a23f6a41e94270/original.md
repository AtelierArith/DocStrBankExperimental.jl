```
crosscov(x, y, [lags]; demean=true)
```

Compute the cross covariance function (CCF) between real-valued vectors or matrices `x` and `y`, optionally specifying the `lags`. `demean` specifies whether the respective means of `x` and `y` should be subtracted from them before computing their CCF.

If both `x` and `y` are vectors, return a vector of the same length as `lags`. Otherwise, compute cross covariances between each pairs of columns in `x` and `y`.

When left unspecified, the lags used are the integers from `-min(size(x,1)-1, 10*log10(size(x,1)))` to `min(size(x,1), 10*log10(size(x,1)))`.

The output is not normalized. See [`crosscor`](@ref) for a function with normalization.
