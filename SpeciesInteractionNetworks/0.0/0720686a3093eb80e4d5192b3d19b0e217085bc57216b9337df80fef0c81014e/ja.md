```
betadiversity(::Type{βWN},U::T,V::T) where {T <: SpeciesInteractionNetwork{<:Partiteness, <:Binary}}
```

ネットワーク間のβ多様性。デフォルトでは、これは全体のネットワークに対する種の非類似性を返します。オプションの最後の引数 `dims` を使用して、上位 (`1`) および下位 (`2`) レベルを指定できます。
