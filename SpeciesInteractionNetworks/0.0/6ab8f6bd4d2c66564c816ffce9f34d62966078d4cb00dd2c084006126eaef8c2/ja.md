```
betadiversity(::Type{βS},U::T,V::T,dims::Integer = 0,) where {T <: SpeciesInteractionNetwork{<:Partiteness, <:Binary}}
```

ネットワーク間の種レベルのβ多様性。デフォルトでは、これはネットワーク全体の種の非類似性を返します。オプションの最後の引数 `dims` を使用して、上位 (`1`) および下位 (`2`) レベルを指定できます。
