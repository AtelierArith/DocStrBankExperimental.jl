```julia
TBModel{T=ComplexF64}(lat::AbstractMatrix{Float64}, site_positions::Matrix{Float64},
    orbital_types::Vector{Vector{Int64}}; isspinful::Bool=false, isorthogonal::Bool=true,
    is_canonical_ordered::Bool=false) where T <: Number
```

Construct a TBModel.

Overlap matrix is automatically set as identity for R = [0, 0, 0] no matter the model is orthogonal or not. Diagonal elements of the position matrix for R = [0, 0, 0] is set according to `site_positions`.
