```
pathbetween(N::SpeciesInteractionNetwork{<:Partiteness{T}, <:Interactions}, source::T, target::T) where {T}
```

`source`と`target`の間のパスを返します。デフォルトのアルゴリズムとして[`BellmanFord`](@ref)を使用します。
