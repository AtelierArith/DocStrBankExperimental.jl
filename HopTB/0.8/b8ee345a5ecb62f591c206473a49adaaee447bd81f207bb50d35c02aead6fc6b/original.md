```julia
sethopping!(tm::TBModel{T}, R::AbstractVector{<:Integer}, n::Int64, m::Int64,
    hopping::Number) where T
```

Set ⟨0n|H|Rm⟩ to `hopping` for `tm`.
