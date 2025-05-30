```
RidgeRegressionSlope(; lambda = 0.0) → rr
```

Return a [`PrecomputableFunction`](@ref) containing all the necessary fields to generate a [`PrecomputedRidgeRegressionSlope`](@ref). `rr` can be used as a change metric focused on trend.

`lambda` is a regularization constant, usually between `0` and `1`.
