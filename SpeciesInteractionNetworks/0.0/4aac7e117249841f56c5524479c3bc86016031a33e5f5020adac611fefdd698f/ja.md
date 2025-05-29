```
render(::Type{Quantitative{T}}, N::SpeciesInteractionNetwork{<:Partiteness, <:Interactions}) where {T <: Number}
```

ネットワークの定量的バージョンを返します。ここで、相互作用の強さは型 `T` です。これは、定量的ネットワークを異なる数値表現に変換するために使用できます。
