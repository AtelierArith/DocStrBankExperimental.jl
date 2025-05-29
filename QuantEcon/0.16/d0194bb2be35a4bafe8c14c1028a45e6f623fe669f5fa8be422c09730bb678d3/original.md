Computes nodes and weights for multivariate normal distribution.

##### Arguments

  * `n::Union{Int, Vector{Int}}` : Number of desired nodes along each dimension
  * `mu::Union{Real, Vector{Real}}` : Mean along each dimension
  * `sig2::Union{Real, Vector{Real}, Matrix{Real}}(eye(length(n)))` : Covariance structure

##### Returns

  * `nodes::Array{Float64}` : An array of quadrature nodes
  * `weights::Array{Float64}` : An array of corresponding quadrature weights

##### Notes

This function has many methods. I try to describe them here.

`n` or `mu` can be a vector or a scalar. If just one is a scalar the other is repeated to match the length of the other. If both are scalars, then the number of repeats is inferred from `sig2`.

`sig2` can be a matrix, vector or scalar. If it is a matrix, it is treated as the covariance matrix. If it is a vector, it is considered the diagonal of a diagonal covariance matrix. If it is a scalar it is repeated along the diagonal as many times as necessary, where the number of repeats is determined by the length of either `n` and/or `mu` (which ever is a vector).

If all 3 are scalars, then 1d nodes are computed. `mu` and `sig2` are treated as the mean and variance of a 1d normal distribution

##### References

Miranda, Mario J, and Paul L Fackler. Applied Computational Economics and Finance, MIT Press, 2002.
