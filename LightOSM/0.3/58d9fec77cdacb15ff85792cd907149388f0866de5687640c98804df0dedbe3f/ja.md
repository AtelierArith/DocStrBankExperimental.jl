```
nearest_way(g, point, [search_radius])
```

ポイントから最も近い道を `SpatialIndexing.jl` R-tree を使用して見つけます。

検索エリアは、`point` を中心とした辺の長さが `2 * search_radius` の立方体です。`search_radius` が指定されていない場合は、最も近いノードまでの距離から自動的に決定されます。

より大きな `search_radius` は、より多くの道の最も近いポイントをチェックする必要があるため、パフォーマンスにペナルティを課します。この値は、目的に応じて慎重に選択してください。

# 引数

  * `g::OSMGraph`: グラフコンテナ。
  * `point`: `GeoLocation` または `[lat, lon, alt]` としての単一ポイント。
  * `search_radius::AbstractFloat`: `point` の周りを検索する立方体のサイズ。

# 戻り値

  * `::Tuple{<:Integer,Float64,EdgePoint}`: 最も近い道が見つかった場合。

      * `::Integer`: 最も近い道のID。
      * `::Float64`: 最も近い道までの距離。
      * `::EdgePoint`: 最も近い道の最も近いポイント。
  * `::Tuple{Nothing,Nothing,Nothing}`: `search_radius` 内に道が見つからなかった場合。
