```
edges(sim, id::AgentID, ::Type{E})
```

エッジのタイプ `E` を持つエージェント `id` をターゲットとして返します。`E` がヒント :SingleEdge を持つ場合は単一のエッジを返し、それ以外の場合はこれらのエッジのベクターを返します。

エージェント `id` をターゲットとするエッジが存在しない場合、`edges` は `nothing` を返します。

`E` がヒント :IgnoreFrom または :Stateless を持つ場合、`edges` は定義されていません。

他にも [`apply!`](@ref)、[`neighborids`](@ref)、[`edgestates`](@ref)、[`num_edges`](@ref)、[`has_edge`](@ref) および [`neighborstates`](@ref) を参照してください。
