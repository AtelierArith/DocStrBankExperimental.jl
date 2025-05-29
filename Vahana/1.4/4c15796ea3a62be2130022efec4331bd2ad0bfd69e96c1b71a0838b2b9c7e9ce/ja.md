```
edgestates(sim, id::AgentID, ::Type{E})
```

エッジの状態を返します。エッジのタイプ `E` がヒント :SingleEdge を持つ場合、エージェント `id` をターゲットとします。それ以外の場合は、これらの状態のベクトルを返します。

エージェント `id` をターゲットとするエッジが存在しない場合、`edgestates` は `nothing` を返します。

`E` がヒント :Stateless を持つ場合、`edgestates` は定義されていません。

!!! tip
    エッジタイプ `E` が :Stateless または :SingleEdge ヒントを持たない場合、`edgestates` は状態のベクトルのためにメモリを割り当てます。この割り当てを避けるために、代わりに `edgestates_iter` を使用できます。


関連情報として [`apply!`](@ref), [`edges`](@ref), [`neighborids`](@ref), [`num_edges`](@ref), [`has_edge`](@ref) および [`neighborstates`](@ref) を参照してください。
