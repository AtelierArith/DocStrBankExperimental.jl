```
invlogcdf(d::UnivariateDistribution, lp::Real)
```

The (generalized) inverse function of [`logcdf`](@ref).

For a given `lp ≤ 0`, `invlogcdf(d, lp)` is the smallest value `x` in the support of `d` for which `logcdf(d, x) ≥ lp`.
