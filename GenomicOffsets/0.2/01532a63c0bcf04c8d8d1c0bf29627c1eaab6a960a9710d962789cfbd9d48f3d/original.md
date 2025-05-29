```
genomic_offset(model::GradientForestGO, X::AbstractMatrix{T}, Xpred::AbstractMatrix{T}) where T<:Real
```

Compute the Gradient Forest genomic offset. Attention! Our implementation does not perform extrapolation, which means that you may obtain unpredictable results if you try so. 

# Arguments

  * `model::GradientForestGO`: A GeometricGO model.
  * `X::AbstractMatrix{T}`: NxP matrix with environmental data. Data will be scaled and centered if the model was fitted with center and scale set to true.
  * `Xpred::Matrix{T}`: NxP matrix with the predicted / altered environmental matrix. Data will be scaled and centered if the model was fitted with center and scale set to true.

# Returns

  * A Vector{Float64} of length N with the Gradient forest genomic offset values.
