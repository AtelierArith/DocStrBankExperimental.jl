```
barycentric_differentiation_matrix(x::AbstractVector{TF}, w::AbstractVector{TF}, k::Integer=1, t::Union{AbstractVector{TF},Nothing}=nothing) where {TF<:AbstractFloat}
```

Compute the barycentric differentiation matrix.

# Arguments

  * `x::AbstractVector{TF}` : Vector of interpolation points
  * `w::AbstractVector{TF}` : Barycentric weights of the interpolation points
  * `k::Integer` : Order of the derivative (default: 1)
  * `t::AbstractVector{TF}` : Vector of angles (default: nothing)

# References:

  * [chebfun/@chebcolloc/baryDiffMat.m at master · chebfun/chebfun](https://github.com/chebfun/chebfun/blob/master/%40chebcolloc/baryDiffMat.m)
  * [Baltensperger2003](@citet*)
