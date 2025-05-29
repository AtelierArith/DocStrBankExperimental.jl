```
neighborstates(sim::Simulation, id::AgentID, ::Type{E}, ::Type{A})
```

エッジのタイプ `E` のソースにおいて、エージェント `id` をターゲットとするエージェントの状態を、タイプ `A` で返します。`E` にヒント :SingleEdge がある場合は1つの状態を返し、そうでない場合はこれらのエージェント状態のベクトルを返します。

エージェント `id` をターゲットとするエッジが存在しない場合、`neighborstates` は `nothing` を返します。

エッジのソース側に異なるタイプのエージェントが存在し、Type{A} を特定できない場合は、代わりに [`neighborstates_flexible`](@ref) を使用できます。

`neighborstates` は T にヒント :IgnoreFrom がある場合は定義されていません。

!!! tip
    エッジタイプ `E` に :SingleEdge ヒントがない場合、`neighborstates` はエージェント状態のベクトルのためにメモリを割り当てます。この割り当てを避けるために、代わりに `neighborstates_iter` を使用できます。


関連情報としては、[`apply!`](@ref)、[`edges`](@ref)、[`neighborids`](@ref)、[`num_edges`](@ref)、[`has_edge`](@ref)、および [`edgestates`](@ref) があります。
