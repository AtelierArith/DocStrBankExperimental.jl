Computes nodes and weights for beta distribution.

##### Arguments

  * `n::Union{Int, Vector{Int}}` : Number of desired nodes along each dimension
  * `a::Union{Real, Vector{Real}}` : First parameter of the beta distribution, along each dimension
  * `b::Union{Real, Vector{Real}}` : Second parameter of the beta distribution, along each dimension

##### Returns

  * `nodes::Array{Float64}` : An array of quadrature nodes
  * `weights::Array{Float64}` : An array of corresponding quadrature weights

##### Notes

If any of the parameters to this function are scalars while others are vectors of length `n`, the the scalar parameter is repeated `n` times.

##### References

Miranda, Mario J, and Paul L Fackler. Applied Computational Economics and Finance, MIT Press, 2002.
