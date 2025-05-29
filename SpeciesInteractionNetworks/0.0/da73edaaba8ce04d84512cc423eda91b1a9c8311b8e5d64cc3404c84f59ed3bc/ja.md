```
render(::Type{Probabilistic{T}}, N::SpeciesInteractionNetwork{<:Partiteness, <:Interactions}) where {T <: AbstractFloat}
```

ネットワークの確率的バージョンを返します。ここで、相互作用の確率は型 `T` です。これは、確率的ネットワークを異なる数値表現に変換するために使用できます。
