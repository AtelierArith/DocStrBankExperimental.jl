```
iscov(x::AbstractMatrix{T}) where {T<:Real}
```

Checks if a given matrix is a valid covariance matrix. A valid covariance matrix must be square, symmetric, and positive semi-definite.

# Arguments

  * `x::AbstractMatrix{T}`: Input matrix to check.

# Returns

  * `Bool`: `true` if the matrix is a valid covariance matrix, `false` otherwise.
