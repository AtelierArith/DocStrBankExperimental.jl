```
Centered()
```

Used in conjunction with `SparseVariationalApproximation`. States that the `q` field of [`SparseVariationalApproximation`](@ref) is to be interpreted directly as the approximate posterior over the pseudo-points.

This is also known as the "unwhitened" parametrization [1].

See also [`NonCentered`](@ref).

[1] - https://en.wikipedia.org/wiki/Whitening_transformation
