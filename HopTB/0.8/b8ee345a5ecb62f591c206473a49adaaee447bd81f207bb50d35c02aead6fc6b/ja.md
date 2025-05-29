```julia
sethopping!(tm::TBModel{T}, R::AbstractVector{<:Integer}, n::Int64, m::Int64,
    hopping::Number) where T
```

⟨0n|H|Rm⟩を`hopping`に設定します。
