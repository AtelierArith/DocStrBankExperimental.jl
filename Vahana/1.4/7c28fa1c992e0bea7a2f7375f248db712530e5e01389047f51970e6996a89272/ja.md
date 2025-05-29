```
neighborids_iter(sim, id::AgentID, ::Type{E})
```

エッジのタイプ `E` のソース側にあるエージェントのIDのイテレータを返します。ターゲットとしてエージェント `id` を持つエッジです。

エージェント `id` をターゲットとするエッジが存在しない場合、関数は `nothing` を返します。

`neighborids` は、`E` がヒント :SingleEdge または :IgnoreFrom の場合には定義されていません。

他にも [`apply!`](@ref)、[`neighborids`](@ref)、[`edges`](@ref)、[`edgestates`](@ref)、[`num_edges`](@ref)、[`has_edge`](@ref) および [`neighborstates`](@ref) を参照してください。
