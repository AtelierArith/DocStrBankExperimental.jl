```julia
setoverlap!(tm::TBModel{T}, R::AbstractVector{<:Integer}, n::Int64, m::Int64,
    overlap::Number) where T
```

Set ⟨0n|Rm⟩ to `overlap` for `tm`.
