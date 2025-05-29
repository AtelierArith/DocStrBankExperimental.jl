```
clrcov(table)
```

Return the centered log-ratio covariance matrix `Γ` of the `table` such that:

  * `Γ[i,j] = cov(log(x[i]/g(x)), log(x[j]/g(x)))` for `i, j = 1, ..., D`,

where `g(x)` is the geometric mean.
