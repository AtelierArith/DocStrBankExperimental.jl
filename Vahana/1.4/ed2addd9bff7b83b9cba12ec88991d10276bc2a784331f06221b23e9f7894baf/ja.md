```
neighborstates_flexible_iter(sim::Simulation, id::AgentID, ::Type{E})
```

エッジのソースにあるエージェントの状態のイテレータを返します。エッジのタイプは `E` で、ターゲットはエージェント `id` です。

エージェント `id` をターゲットとするエッジが存在しない場合、関数は `nothing` を返します。

`neighborstates_flexible_iter` は [`neighborstates_iter`](@ref) の型不安定バージョンであり、エージェントの型が特定できない場合にのみ使用するべきです。

`neighborstates_flexible_iter` は、T がヒント :IgnoreFrom またはヒント :SingleEdge を持つ場合には定義されません。

他にも [`neighborstates_flexible`](@ref)、[`apply!`](@ref)、[`edges`](@ref)、[`neighborids`](@ref)、[`num_edges`](@ref)、[`has_edge`](@ref) および [`edgestates`](@ref) を参照してください。
