```
StatsAPI.confint(x::PowerTransformation; level::Real=0.95, fast::Bool=nobs(bc) > 10_000)
```

Compute confidence intervals for λ, with confidence level level (by default 95%).

If `fast`, then a symmetric confidence interval around ̂λ is assumed and the upper bound is computed using the difference between the lower bound and λ. Symmetry is generally a safe assumption for approximate values and halves computation time.

If not `fast`, then the lower and upper bounds are computed separately.
