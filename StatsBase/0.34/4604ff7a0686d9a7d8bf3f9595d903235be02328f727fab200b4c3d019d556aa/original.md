```
pacf(X, lags; method=:regression)
```

Compute the partial autocorrelation function (PACF) of a real-valued vector or matrix `X` at `lags`. `method` designates the estimation method. Recognized values are `:regression`, which computes the partial autocorrelations via successive regression models, and `:yulewalker`, which computes the partial autocorrelations using the Yule-Walker equations.

If `x` is a vector, return a vector of the same length as `lags`. If `x` is a matrix, return a matrix of size `(length(lags), size(x, 2))`, where each column in the result corresponds to a column in `x`.
