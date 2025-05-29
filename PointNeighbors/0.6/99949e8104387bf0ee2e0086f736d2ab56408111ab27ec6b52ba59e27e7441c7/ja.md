```
TrivialNeighborhoodSearch{NDIMS}(; search_radius = 0.0, eachpoint = 1:0,
                                 periodic_box = nothing)
```

単純にすべての点をループするトリビアルな近傍探索。

# 引数

  * `NDIMS`: 次元数。

# キーワード

  * `search_radius = 0.0`:    固定された探索半径。デフォルトの `0.0` は、                           [`copy_neighborhood_search`](@ref) と一緒に使用するのに便利です。
  * `eachpoint = 1:0`:        すべての点のインデックスのイテレータ。通常は `1:n_points` です。                           デフォルトの `1:0` は、                           [`copy_neighborhood_search`](@ref) と一緒に使用するのに便利です。
  * `periodic_box = nothing`: (長方形の)周期的な領域を使用するには、                           [`PeriodicBox`](@ref) を渡してください。
