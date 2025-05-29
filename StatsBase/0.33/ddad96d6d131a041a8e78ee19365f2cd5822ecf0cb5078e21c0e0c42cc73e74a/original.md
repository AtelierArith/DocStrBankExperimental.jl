```
SimpleCovariance(;corrected::Bool=false)
```

Simple covariance estimator. Estimation calls `cov(x; corrected=corrected)`, `cov(x, y; corrected=corrected)` or `cov(X, w, dims; corrected=corrected)` where `x`, `y` are vectors, `X` is a matrix and `w` is a weighting vector.
