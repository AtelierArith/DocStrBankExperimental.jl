```
half(::Type{Logistic}) :: Logistic
half(::Type{Logistic{T}}) where {T<:AbstractFloat} :: Logistic{T}
half(::Logistic{T}) where {T<:AbstractFloat} :: Logistic{T}
```

Return a `Logistic` number equal to a half.

# Examples

```jldoctest
julia> (logisticate(0) + logisticate(1)) / 2
Logistic{Float64}(0.0) ≈ 0.5

julia> half(Logistic{Float64})
Logistic{Float64}(0.0) ≈ 0.5
```
