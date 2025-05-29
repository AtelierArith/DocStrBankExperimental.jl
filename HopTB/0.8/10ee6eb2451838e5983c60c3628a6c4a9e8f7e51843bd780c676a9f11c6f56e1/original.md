```julia
TBModel{T=ComplexF64}(norbits::Int64, lat::AbstractMatrix{Float64};
    isorthogonal::Bool=true) where T <: Number
```

Construct a TBModel.

Overlap matrix is automatically set as identity for R = [0, 0, 0] no matter the model is orthogonal or not. All extra information is missing. 
