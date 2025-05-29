```
num_edges(sim, id::AgentID, ::Type{E})
```

エージェント `id` をターゲットとするタイプ `E` のエッジの数を返します。

`num_edges` は T がヒント :SingleEdge の場合には定義されていません。

また、[`apply!`](@ref)、[`edges`](@ref)、[`neighborids`](@ref)、[`edgestates`](@ref)、[`has_edge`](@ref) および [`neighborstates`](@ref) も参照してください。
