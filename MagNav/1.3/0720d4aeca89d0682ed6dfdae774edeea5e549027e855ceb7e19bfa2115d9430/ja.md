```
map_check(map_map::Map, lat, lon, alt = fill(median(map_map.alt),size(lat)))
```

与えられた地図上に緯度と経度のポイントがあるか確認します。

**引数:**

  * `map_map`: `Map` 磁気異常マップ構造体
  * `lat`:     緯度  [ラジアン]
  * `lon`:     経度 [ラジアン]
  * `alt`:     （オプション）高度 [メートル]、`MapS3D` のみで使用されます

**戻り値:**

  * `bool`: true の場合、すべての `lat` & `lon` (& `alt`) ポイントが `map_map` 上にあります
