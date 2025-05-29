```
half(::Type{Logistic}) :: Logistic
half(::Type{Logistic{T}}) where {T<:AbstractFloat} :: Logistic{T}
half(::Logistic{T}) where {T<:AbstractFloat} :: Logistic{T}
```

半分に等しい `Logistic` 数を返します。

# 例

```jldoctest
julia> (logisticate(0) + logisticate(1)) / 2
Logistic{Float64}(0.0) ≈ 0.5

julia> half(Logistic{Float64})
Logistic{Float64}(0.0) ≈ 0.5
```
