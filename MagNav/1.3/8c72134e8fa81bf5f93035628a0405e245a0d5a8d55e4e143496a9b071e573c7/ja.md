```
map_get_gxf(map_gxf::String)
```

ArchGDALを使用してGXFファイルからマップデータを読み込みます。

**引数:**

  * `map_gxf`: マップGXFファイルのパス/名前（`.gxf`拡張子は省略可能）

**戻り値:**

  * `map_map`: `ny` x `nx` 2Dグリッドマップデータ
  * `map_xx`:  `nx`マップx方向（経度）座標
  * `map_yy`:  `ny`マップy方向（緯度）座標
