```
acf!(r, x, lags; demean=false, normalize=false)
```

Evaluate the autocorrelation of `x` at time `lags` in-place and store output in `r`. See `acf`. For this in-place version, `lags` *must* be specified, and `length(r)==length(lags)`.
