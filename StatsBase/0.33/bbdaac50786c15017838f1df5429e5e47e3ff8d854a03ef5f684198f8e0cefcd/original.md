```
crosscor(x, y, [lags]; demean=true)
```

Compute the cross correlation between real-valued vectors or matrices `x` and `y`, optionally specifying the `lags`. `demean` specifies whether the respective means of `x` and `y` should be subtracted from them before computing their cross correlation.

If both `x` and `y` are vectors, return a vector of the same length as `lags`. Otherwise, compute cross covariances between each pairs of columns in `x` and `y`.

When left unspecified, the lags used are the integers from `-min(size(x,1)-1, 10*log10(size(x,1)))` to `min(size(x,1), 10*log10(size(x,1)))`.

The output is normalized by `sqrt(var(x)*var(y))`. See [`crosscov`](@ref) for the unnormalized form.
