```
invlogccdf(d::UnivariateDistribution, lp::Real)
```

[`logccdf`](@ref) の（一般化された）逆関数です。

与えられた `lp ≤ 0` に対して、`invlogccdf(d, lp)` は `logccdf(d, x) ≤ lp` となる `d` のサポート内の最小の値 `x` です。
