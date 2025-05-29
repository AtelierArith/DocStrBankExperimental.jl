```
mean_and_cov(d::StateSpaceSet) → μ, m::SMatrix
```

Return a tuple of the column means `μ` and covariance matrix `m`.

Column means are always computed for the covariance matrix, so this is faster than computing both quantities separately.
