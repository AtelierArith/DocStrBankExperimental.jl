```
cutoff(M::AbstractVecOrMat{T}, α::T, weighted::Bool=false) where {T<:AbstractFloat}
```

Transform the vector or matrix `X` based in SimSpread's similarity cutoff function.

# Arguments

  * `X::AbstractVecOrMat{AbstractFloat}` : Matrix or Vector to transform
  * `α::AbstractFloat` : Similarity cutoff
  * `weighted::Bool` : Apply weighting function to outcome (default = false)
