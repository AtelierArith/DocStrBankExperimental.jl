```
quantreg(X, y, args...; kwargs...)
```

An alias for `fit(QuantileRegression, X, y; kwargs...)`.

The arguments `X` and `y` can be a `Matrix` and a `Vector` or a `Formula` and a `DataFrame`.
