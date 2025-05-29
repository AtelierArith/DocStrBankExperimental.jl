```
cov(d::StateSpaceSet) → m::SMatrix
```

Compute the covariance matrix `m` from the columns of `d`, where `m[i, j]` is the covariance between `d[:, i]` and `d[:, j]`.
