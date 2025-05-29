```
xcov(x, y, [lags]; demean=true)
```

Compute the cross covariance function (CCF) between real-valued vectors or matrices `x` and `y`, optionally specifying the `lags`. `demean` specifies whether the respective means of `x` and `y` should be subtracted from them before computing their CCF.

If both x and y are vectors, return a vector of the same length as lags. Otherwise, compute cross covariances between each pairs of columns in x and y.

### Kwargs

  * `demean`: Specifies whether the respective means of x and y should be subtracted from them before  computing their cross covariance.
  * `lags`: When left unspecified and `maxlags=0`, the lags used are the integers from  `-min(size(x,1)-1, 10*log10(size(x,1))) to min(size(x,1), 10*log10(size(x,1)))`
  * `maxlags`: limits the lag range from `-maxlag` to `maxlag`.
