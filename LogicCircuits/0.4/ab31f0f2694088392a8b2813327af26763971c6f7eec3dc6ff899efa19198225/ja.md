```
and(α::Bdd, β::Bdd)::Bdd
and(x::Integer, β::Bdd)::Bdd
and(α::Bdd, x::Integer)::Bdd
and(x::Integer, y::Integer)::Bdd
and(Φ::Vararg{Bdd})::Bdd
and(Φ::AbstractVector{Bdd})::Bdd
and(Φ::Vararg{T})::Bdd where T <: Integer
and(Φ::AbstractVector{T})::Bdd where T <: Integer
and(Φ::Vararg{Union{T, Bdd}})::Bdd where T <: Integer
```

与えられたブール関数の論理積を返します。
