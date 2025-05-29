```
quantile(d::UnivariateDistribution, q::Real)
```

`q`で（一般化された）逆累積分布関数を評価します。

与えられた `0 ≤ q ≤ 1` に対して、`quantile(d, q)` は `cdf(d, x) ≥ q` となる `d` のサポート内の最小値 `x` です。

関連情報: [`cquantile`](@ref), [`invlogcdf`](@ref), および [`invlogccdf`](@ref)。
