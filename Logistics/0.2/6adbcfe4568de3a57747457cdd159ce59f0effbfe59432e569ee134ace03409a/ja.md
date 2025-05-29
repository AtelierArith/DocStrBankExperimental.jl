```
logisticate(x::Real) :: Logistic
logisticate(T::Type{<:AbstractFloat}, x::Real) :: Logistic{T}
logisticate(::Type{Logistic}, x::Real) :: Logistic
logisticate(::Type{<:Logistic{T}}, x::Real) 
	where {T<:AbstractFloat} :: Logistic{T}

`Real` 数をその等価の `Logistic` 数に変換します。

# 例

```

jldoctest julia> logisticate(0.39) Logistic{Float64}(-0.4473122180436648) ≈ 0.39

julia> logisticate(Float32, 0.39) Logistic{Float32}(-0.4473123) ≈ 0.39

julia> logisticate(Logistic, 0.39) Logistic{Float64}(-0.4473122180436648) ≈ 0.39

julia> logisticate(Logistic{Float32}, 0.39) Logistic{Float32}(-0.4473123) ≈ 0.39 ```
