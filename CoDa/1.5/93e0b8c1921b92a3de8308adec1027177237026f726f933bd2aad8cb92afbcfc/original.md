```
alrcov(table)
```

Return the log-ratio covariance matrix `Σ` of the `table` such that:

  * `Σ[i,j] = cov(log(x[i]/x[D]), log(x[j]/x[D]))` for `i, j = 1, ..., d`
