```
genomic_offset(model::GeometricGO, X::AbstractMatrix{T}, Xpred::AbstractMatrix{T}) where T<:Real
```

Compute the Geometric genomic offset.

# Arguments

  * `model::GeometricGO`: A GeometricGO model.
  * `X::AbstractMatrix{T}`: NxP matrix with environmental data. Data will be scaled and centered if the model was fitted with center and scale set to true.
  * `Xpred::Matrix{T}`: NxP matrix with the predicted / altered environmental matrix. Data will be scaled and centered if the model was fitted with center and scale set to true.
  * `candidates::AbstractVector{Integer}`: Indices of the candidate loci.

# Returns

  * A Vector{Float64} of length N with the Geometric genomic offset values.
