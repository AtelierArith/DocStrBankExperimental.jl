```
acf(x [, lags]; demean=false, normalize=false)
```

Evaluate the autocorrelation function of signal `x`.

By default, the acf is evaluated at all available lags `0:size(x,1)-1`, but arbitrary `lags` can be optionally specified.

**Keywords**

  * `demean`: whether to subtract the mean of `x` before evaluating the acf
  * `normalize`: whether to normalize the acf to its lag-0 value

When `length(x) < 1024`, a raw computation (`dotacf`) is used, whereas a FFT-based algorithm is used for larger arrays (`fftacf`).
