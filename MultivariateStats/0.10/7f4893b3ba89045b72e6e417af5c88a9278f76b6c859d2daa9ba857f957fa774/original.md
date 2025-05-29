```
cov_whitening(C, regcoef)
```

Derive a whitening transform based on a regularized covariance, as `C + (eigmax(C) * regcoef) * eye(d)`.
