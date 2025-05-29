```
has_edge(sim, id::AgentID, ::Type{E})
```

エージェント `id` をターゲットとするタイプ `E` のエッジが少なくとも1つ存在する場合は true を返します。

`has_edge` は、T が :SingleEdge および :SingleType ヒントを持つ場合には定義されていませんが、:IgnoreFrom および :Stateless ヒントも持つ場合は例外です。

関連情報として [`apply!`](@ref)、[`edges`](@ref)、[`neighborids`](@ref)、[`edgestates`](@ref)、[`num_edges`](@ref) および [`neighborstates`](@ref) を参照してください。
