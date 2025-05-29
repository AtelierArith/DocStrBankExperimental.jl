```
map_fill(map_map::Matrix, map_xx::Vector, map_yy::Vector; k::Int = 3)
```

欠損している地図データを埋める。

**引数:**

  * `map_map`: `ny` x `nx` 2D グリッドマップデータ
  * `map_xx`:  `nx` マップの x 方向（経度）座標
  * `map_yy`:  `ny` マップの y 方向（緯度）座標
  * `k`:       （オプション）k近傍法のための最近傍数

**戻り値:**

  * `map_map`: `ny` x `nx` 2D グリッドマップデータ、埋められたもの
