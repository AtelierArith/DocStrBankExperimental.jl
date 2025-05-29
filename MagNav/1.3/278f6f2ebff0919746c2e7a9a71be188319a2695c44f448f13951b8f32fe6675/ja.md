```
map_resample(map_map::Matrix, map_xx::Vector, map_yy::Vector,
             map_mask::BitMatrix, map_xx_new::Vector, map_yy_new::Vector)
```

新しいグリッドでマップを再サンプリングします。

**引数:**

  * `map_map`:    `ny` x `nx` 2D グリッドマップデータ
  * `map_xx`:     `nx` マップの x 方向（経度）座標
  * `map_yy`:     `ny` マップの y 方向（緯度）座標
  * `map_mask`    `ny` x `nx` 有効（未入力）マップデータのマスク
  * `map_xx_new`: `nx_new` 再サンプリングに使用するマップの x 方向（経度）座標
  * `map_yy_new`: `ny_new` 再サンプリングに使用するマップの y 方向（緯度）座標

**戻り値:**

  * `map_map`:  `ny_new` x `nx_new` 2D グリッドマップデータ、再サンプリング済み
  * `map_mask`: `ny_new` x `nx_new` 有効（未入力）マップデータのマスク、再サンプリング済み
