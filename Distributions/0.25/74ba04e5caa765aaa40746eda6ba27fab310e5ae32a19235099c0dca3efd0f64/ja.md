```
invlogcdf(d::UnivariateDistribution, lp::Real)
```

[`logcdf`](@ref) の（一般化された）逆関数です。

与えられた `lp ≤ 0` に対して、`invlogcdf(d, lp)` は `logcdf(d, x) ≥ lp` となる `d` のサポート内の最小値 `x` です。
