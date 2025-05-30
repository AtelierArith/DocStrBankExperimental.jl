```
shortestpath(N::SpeciesInteractionNetwork{<:Partiteness{T}, <:Interactions}, sp::T)
```

最短経路アルゴリズムにはデフォルトで [`BellmanFord`](@ref) が使用されます。 [`Dijkstra`](@ref) も参照してください。

[`pathbetween`](@ref) と連携するためには、[`shortestpath`](@ref) のすべてのオーバーロードが `include_paths` キーワード引数を受け入れる必要があります。この引数が `true` の場合、到達した各ノードの前任者を示す *第二* の辞書を返します。
