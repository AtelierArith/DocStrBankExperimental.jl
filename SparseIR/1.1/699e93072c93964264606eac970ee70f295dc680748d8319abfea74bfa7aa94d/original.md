```
fit!(buffer::Array{S,N}, smpl::AbstractSampling, al::Array{T,N}; 
    dim=1, workarr::Vector{S}) where {S,T,N}
```

Like [`fit`](@ref), but write the result to `buffer`. Use `dim = 1` or `dim = N` to avoid allocating large temporary arrays internally. The length of `workarr` cannot be smaller than [`SparseIR.workarrlength`](@ref)`(smpl, al)`.
