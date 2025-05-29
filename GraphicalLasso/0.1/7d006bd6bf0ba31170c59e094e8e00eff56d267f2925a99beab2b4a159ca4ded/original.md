```
randsparsecov(p, thr)
```

Generates a random sparse covariance matrix of size `p x p` with a specified threshold for sparsity.

# Arguments

  * `p::Int`: The dimension of the covariance matrix.
  * `thr::Real`: Threshold value for sparsity. Values below this threshold will be set to zero.

# Returns

  * `Hermitian{Float64}`: A sparse covariance matrix.
