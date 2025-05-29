```
genomic_offset(model::RONA, X::AbstractMatrix{T}, Xpred::AbstractMatrix{T}) where T<:Real
```

Compute the genomic offset for the RONA model.

# Arguments

  * `model::RONA`: A RONA model.
  * `X::AbstractMatrix{T}`: NxP matrix with environmental data.
  * `Xpred::Matrix{T}`: NxP matrix with the predicted / altered environmental matrix.

# Returns

  * A Vector{Float64} of length N with the RONA genomic offset values.
