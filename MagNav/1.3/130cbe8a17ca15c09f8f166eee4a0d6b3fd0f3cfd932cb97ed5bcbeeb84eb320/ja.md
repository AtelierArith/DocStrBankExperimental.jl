```
get_cached_map(map_cache::Map_Cache, lat::Real, lon::Real, alt::Real;
               silent::Bool = false)
```

特定の位置でキャッシュされたマップを取得します。

**引数:**

  * `map_cache`: `Map_Cache` マップキャッシュ構造体
  * `lat`:       緯度  [rad]
  * `lon`:       経度 [rad]
  * `alt`:       高度  [m]
  * `silent`:    （オプション）trueの場合、出力は行われません

**戻り値:**

  * `itp_mapS`: スカラーマップ補間関数 (`f(lat,lon)` at `alt`)
