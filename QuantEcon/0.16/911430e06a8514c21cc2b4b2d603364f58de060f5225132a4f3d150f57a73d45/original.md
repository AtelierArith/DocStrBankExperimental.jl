Computes quadrature nodes and weights for multivariate uniform distribution

##### Arguments

  * `n::Union{Int, Vector{Int}}` : Number of desired nodes along each dimension
  * `mu::Union{Real, Vector{Real}}` : Mean along each dimension
  * `sig2::Union{Real, Vector{Real}, Matrix{Real}}(eye(length(n)))` : Covariance structure

##### Returns

  * `nodes::Array{Float64}` : An array of quadrature nodes
  * `weights::Array{Float64}` : An array of corresponding quadrature weights

##### Notes

See also the documentation for `qnwnorm`

##### References

Miranda, Mario J, and Paul L Fackler. Applied Computational Economics and Finance, MIT Press, 2002.
