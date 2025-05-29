```
NonCentered()
```

Used in conjunction with `SparseVariationalApproximation`. States that the `q` field of [`SparseVariationalApproximation`](@ref) is to be interpreted as the approximate posterior over `cholesky(cov(u)).L \ (u - mean(u))`, where `u` are the pseudo-points.

This is also known as the "whitened" parametrization [1].

See also [`Centered`](@ref).

[1] - https://en.wikipedia.org/wiki/Whitening_transformation
