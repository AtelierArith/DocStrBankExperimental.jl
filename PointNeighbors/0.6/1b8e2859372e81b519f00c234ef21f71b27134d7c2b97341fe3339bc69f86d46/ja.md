```
PrecomputedNeighborhoodSearch{NDIMS}(; search_radius = 0.0, n_points = 0,
                                     periodic_box = nothing, update_strategy = nothing)
```

事前計算された隣接点検索。初期化および更新時に各点のすべての隣接点のリストが計算されます。この隣接点検索は、はるかに遅い[`update!`](@ref)のコストで隣接ループのパフォーマンスを最大化します。

初期化および更新時に隣接点リストを計算するために、内部で[`GridNeighborhoodSearch`](@ref)が使用されます。

# 引数

  * `NDIMS`: 次元数。

# キーワード

  * `search_radius = 0.0`:    固定の検索半径。デフォルトの`0.0`は、[`copy_neighborhood_search`](@ref)と一緒に使用するのに便利です。
  * `n_points = 0`:           総点数。デフォルトの`0`は、[`copy_neighborhood_search`](@ref)と一緒に使用するのに便利です。
  * `periodic_box = nothing`: (長方形の)周期的領域を使用するには、[`PeriodicBox`](@ref)を渡します。
  * `update_strategy`:        内部で使用される`GridNeighborhoodSearch`の`update!`を並列化するための戦略。利用可能なオプションについては、[`GridNeighborhoodSearch`](@ref)を参照してください。
