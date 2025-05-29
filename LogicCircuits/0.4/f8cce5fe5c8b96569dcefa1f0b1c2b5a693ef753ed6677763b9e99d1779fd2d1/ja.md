```
or(α::Bdd, β::Bdd)::Bdd 
or(x::Integer, β::Bdd)::Bdd
or(α::Bdd, x::Integer)::Bdd
or(x::Integer, y::Integer)::Bdd
or(Φ::Vararg{Bdd})::Bdd
or(Φ::AbstractVector{Bdd})::Bdd
or(Φ::Vararg{T})::Bdd where T <: Integer
or(Φ::AbstractVector{T})::Bdd where T <: Integer
or(Φ::Vararg{Union{T, Bdd}})::Bdd where T <: Integer
```

与えられたブール関数に対する論理和を返します。
