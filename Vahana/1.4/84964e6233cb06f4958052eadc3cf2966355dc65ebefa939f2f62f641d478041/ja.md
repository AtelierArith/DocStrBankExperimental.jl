```
neighborstates_flexible(sim::Simulation, id::AgentID, ::Type{E})
```

エッジのタイプ `E` のソースにあるエージェントの状態を、ターゲットとしてエージェント `id` を持つ場合に返します。`E` にヒント :SingleEdge がある場合はその状態を返し、そうでない場合はこれらのエージェントの状態のベクトルを返します。

エージェント `id` をターゲットとするエッジが存在しない場合、`neighborstates_flexible` は `nothing` を返します。

`neighborstates_flexible` は [`neighborstates`](@ref) の型不安定バージョンであり、エージェントの型が特定できない場合にのみ使用するべきです。

`neighborstates_flexible` は T にヒント :IgnoreFrom がある場合には定義されていません。

!!! tip
    エッジタイプ `E` に :SingleEdge ヒントがない場合、`neighborstates_flexible` はエージェントの状態のベクトルのためにメモリを割り当てます。この割り当てを避けるために、代わりに `neighborstates_flexible_iter` を使用できます。


関連情報としては [`apply!`](@ref)、[`edges`](@ref)、[`neighborids`](@ref)、[`num_edges`](@ref)、[`has_edge`](@ref)、および [`edgestates`](@ref) があります。
