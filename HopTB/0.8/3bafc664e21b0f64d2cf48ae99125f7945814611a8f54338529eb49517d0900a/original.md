```julia
TBModel{T=ComplexF64}(lat::AbstractMatrix{Float64}, orbital_positions::AbstractMatrix{Float64};
    isorthogonal::Bool = true) where T <: Number
```

Construct a TBModel.

All extra information is missing. Overlap matrix is automatically set as identity for R = [0, 0, 0] no matter the model is orthogonal or not. Diagonal elements of the position matrix for R = [0, 0, 0] is set to the `orbital_positions`.
