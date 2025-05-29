```
neighborstates_iter(sim::Simulation, id::AgentID, ::Type{E}, ::Type{A})
```

エッジのタイプ `E` のソースにあるエージェントの状態のイテレータを返します。ターゲットとしてエージェント `id` を持つエージェントのタイプ `A` の状態です。

エージェント `id` をターゲットとするエッジが存在しない場合、関数は `nothing` を返します。

エッジのソース側に異なるタイプのエージェントが存在し、Type{A} を特定することが不可能な場合は、代わりに [`neighborstates_flexible_iter`](@ref) を使用できます。

`neighborstates_iter` は、T が :IgnoreFrom または :SingleEdge のヒントを持つ場合には定義されていません。

他にも [`neighborstates`](@ref)、[`apply!`](@ref)、[`edges`](@ref)、[`neighborids`](@ref)、[`num_edges`](@ref)、[`has_edge`](@ref)、および [`edgestates`](@ref) を参照してください。
