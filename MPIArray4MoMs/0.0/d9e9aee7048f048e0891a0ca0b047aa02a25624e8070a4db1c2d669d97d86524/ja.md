```
indice2rank(indice::T, rank2indices::Dict{Integer, NTuple{1}}) where{T<:Integer}
indice2rank(indice::NTuple{N, T}, rank2indices::Dict{Int, Tuple{Vararg{T2, N}}}) where{T<:Integer, N, T2}
indice2ranks(indice::NTuple{N, Union{UnitRange{T}, Vector{T}}}, rank2indices) where{T, N}
```

`rank2indices`から`indice`のランクを取得します。
