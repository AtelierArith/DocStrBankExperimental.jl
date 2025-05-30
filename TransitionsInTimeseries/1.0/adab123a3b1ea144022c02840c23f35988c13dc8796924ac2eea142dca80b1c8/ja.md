```
RidgeRegressionSlope(; lambda = 0.0) → rr
```

Return a [`PrecomputableFunction`](@ref) containing all the necessary fields to generate a [`PrecomputedRidgeRegressionSlope`](@ref). `rr` can be used as a change metric focused on trend.

`lambda`は正則化定数で、通常は`0`と`1`の間です。
