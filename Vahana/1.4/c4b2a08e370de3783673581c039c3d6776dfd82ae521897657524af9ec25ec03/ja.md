```
neighborids(sim, id::AgentID, ::Type{E})
```

エッジのタイプ `E` のソースにあるエージェントのIDを返します。ターゲットがエージェント `id` の場合、`E` がヒント :SingleEdge を持つ場合はそのエージェントのIDを返し、そうでない場合はそれらのエッジのソース側にあるエージェントのIDのベクターを返します。

エージェント `id` をターゲットとするエッジが存在しない場合、`neighborids` は `nothing` を返します。

`E` がヒント :IgnoreFrom を持つ場合、`neighborids` は定義されていません。

!!! tip
    エッジタイプ `E` が :Stateless または :SingleEdge ヒントを持たない場合、`neighborids` はエージェントIDのベクターのためにメモリを割り当てます。この割り当てを避けるために、代わりに `neighborids_iter` を使用できます。


関連情報として [`apply!`](@ref), [`edges`](@ref), [`edgestates`](@ref), [`num_edges`](@ref), [`has_edge`](@ref) および [`neighborstates`](@ref) を参照してください。
