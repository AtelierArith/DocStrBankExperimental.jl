```
pathbetween(::Type{ShortestPathMethod}, N::SpeciesInteractionNetwork{<:Partiteness{T}, <:Interactions}, source::T, target::T) where {T}
```

`source` と `target` の間のパスを返します。結果は相互作用のベクトルとして与えられ、*すなわち* `interactions(N)` の出力のサブセットを `source` から `target` まで示します。
