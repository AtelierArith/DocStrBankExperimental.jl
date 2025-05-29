```
quantile(d::UnivariateDistribution, q::Real)
```

Evaluate the (generalized) inverse cumulative distribution function at `q`.

For a given `0 ≤ q ≤ 1`, `quantile(d, q)` is the smallest value `x` in the support of `d` for which `cdf(d, x) ≥ q`.

See also: [`cquantile`](@ref), [`invlogcdf`](@ref), and [`invlogccdf`](@ref).
