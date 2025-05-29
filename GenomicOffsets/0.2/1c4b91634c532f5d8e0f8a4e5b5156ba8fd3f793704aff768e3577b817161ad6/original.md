```
genomic_offset(model::RDAGO, X::AbstractMatrix{T}, Xpred::AbstractMatrix{T}) where T<:Real
```

Compute the RDA genomic offset.

# Arguments

  * `model::RDAGO`: A RDAGO model.
  * `X::AbstractMatrix{T}`: NxP matrix with environmental data.
  * `Xpred::Matrix{T}`: NxP matrix with the predicted / altered environmental matrix.
  * `weighted::Bool=false`: If true, the euclidean distance in the projected space is weighted based on the eigenvalue of each axis.

# Returns

  * A Vector{Float64} of length N with the RDAGO genomic offset values.
