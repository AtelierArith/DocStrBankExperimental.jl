```
median(d::UnivariateDistribution)
```

Return the median value of distribution `d`. The median is the smallest `x` in the support of `d` for which `cdf(d, x) ≥ 1/2`. Corresponding to this definition as 1/2-quantile, a fallback is provided calling the `quantile` function.
