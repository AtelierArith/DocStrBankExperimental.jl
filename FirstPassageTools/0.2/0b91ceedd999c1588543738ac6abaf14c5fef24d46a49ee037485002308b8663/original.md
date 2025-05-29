```
quantile(d::FPDistribution, p)
```

Return the $p$-th quantile for the first-passage time distribution `d`.

The quantile function for these distributions has no closed-form solution, so this method uses the `find_zero` function from the `Roots` package to find the quantile numerically.
