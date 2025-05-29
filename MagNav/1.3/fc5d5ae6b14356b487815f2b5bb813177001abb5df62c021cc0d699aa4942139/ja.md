```
map_resample(mapS::MapS, map_xx_new::Vector, map_yy_new::Vector)
```

新しいグリッドでマップを再サンプリングします。

**引数:**

  * `mapS`:       `MapS` スカラー磁気異常マップ構造体
  * `map_xx_new`: `nx_new` 再サンプリングに使用するマップのx方向（経度）座標
  * `map_yy_new`: `ny_new` 再サンプリングに使用するマップのy方向（緯度）座標

**戻り値:**

  * `mapS`: `MapS` スカラー磁気異常マップ構造体、再サンプリング済み
