```
nearest_ways(g, point, [search_radius])
```

ポイントから近くの道を `SpatialIndexing.jl` R-tree を使用して見つけます。

検索エリアは、`point` を中心とした辺の長さが `2 * search_radius` の立方体です。

大きな `search_radius` は、より多くの道が最も近いポイントをチェックする必要があるため、パフォーマンスのペナルティを伴います。この値は、目的の使用ケースに応じて慎重に選択してください。

# 引数

  * `g::OSMGraph`: グラフコンテナ。
  * `point`/`points`: `GeoLocation` としての単一ポイントまたは `[lat, lon, alt]`。
  * `search_radius::AbstractFloat=0.1`: `point` の周りを検索する立方体のサイズ。

# 戻り値

  * `::Tuple{Vector{<:Integer},Vector{Float64},Vector{EdgePoint}}`:

      * `::Vector{<:Integer}`: 最も近い道のID。
      * `::Vector{Float64}`: 各対応する近くの道までの距離。
      * `::Vector{EdgePoint}`: 各対応する近くの道の最も近いポイント。
