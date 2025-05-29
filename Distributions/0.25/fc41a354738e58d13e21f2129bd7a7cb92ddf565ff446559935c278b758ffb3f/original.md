```
invlogccdf(d::UnivariateDistribution, lp::Real)
```

The (generalized) inverse function of [`logccdf`](@ref).

For a given `lp ≤ 0`, `invlogccdf(d, lp)` is the smallest value `x` in the support of `d` for which `logccdf(d, x) ≤ lp`.
