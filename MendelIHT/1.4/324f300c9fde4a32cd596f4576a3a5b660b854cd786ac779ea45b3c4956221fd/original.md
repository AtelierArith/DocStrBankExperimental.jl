```
loglikelihood(v::mIHTVariable)
```

Calculates the loglikelihood of observing `Y` given mean `μ` and precision matrix `Γ` (inverse covariance matrix) under a multivariate Gaussian.

Caution: This function mutates storage variables `v.r_by_r1` and `v.r_by_r2`
