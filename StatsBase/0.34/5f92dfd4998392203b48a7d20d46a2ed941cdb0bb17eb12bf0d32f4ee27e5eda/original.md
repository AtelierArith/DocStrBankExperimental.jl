```
pacf!(r, X, lags; method=:regression)
```

Compute the partial autocorrelation function (PACF) of a matrix `X` at `lags` and store the result in `r`. `method` designates the estimation method. Recognized values are `:regression`, which computes the partial autocorrelations via successive regression models, and `:yulewalker`, which computes the partial autocorrelations using the Yule-Walker equations.

`r` must be a matrix of size `(length(lags), size(x, 2))`.
