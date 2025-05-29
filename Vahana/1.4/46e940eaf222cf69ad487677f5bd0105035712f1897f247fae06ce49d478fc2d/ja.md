```
edgestates_iter(sim, id::AgentID, ::Type{E})
```

エッジの状態のイテレータを返します。エッジのタイプは `E` で、エージェント `id` がターゲットです。

エージェント `id` をターゲットとするエッジが存在しない場合、関数は `nothing` を返します。

`edgestates_iter` は、`E` がヒント :Stateless または :SingleEdge の場合は定義されていません。

さらに [`apply!`](@ref), [`edgestates`](@ref), [`edges`](@ref), [`neighborids`](@ref), [`num_edges`](@ref), [`has_edge`](@ref) および [`neighborstates`](@ref) を参照してください。
