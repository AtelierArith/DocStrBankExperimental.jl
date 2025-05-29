```
ZCAcor(X::AbstractMatrix{T}) where {T<:Base.IEEEFloat}
```

Construct a ZCAcor transformer from the from the `q × n` matrix, each row of which is a sample of an `n`-dimensional random variable.

In order for the resultant covariance matrix to be positive definite, `q` must be ≥ `n` and none of the variances may be zero.
