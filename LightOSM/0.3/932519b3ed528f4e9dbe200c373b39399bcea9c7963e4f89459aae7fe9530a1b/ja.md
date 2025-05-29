```
nearest_point_on_way(g::OSMGraph, point::GeoLocation, way_id::DEFAULT_OSM_ID_TYPE)
```

指定された点に最も近い位置を道上で見つけます。`EdgePoint`にマッチします。

# 引数

  * `g::OSMGraph`: LightOSMグラフ。
  * `point::GeoLocation`: 最も近い位置を見つけるための点。
  * `wid::Integer`: 検索する道のID。

# 戻り値

  * `::Tuple`:

      * `::EdgePoint`: 2つのノード間の道に沿った最も近い位置。
      * `::Float64`: `point`から道上の最も近い位置までの距離。
