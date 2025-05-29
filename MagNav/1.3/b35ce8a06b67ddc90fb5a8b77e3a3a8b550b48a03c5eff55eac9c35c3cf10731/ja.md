```
map_fill(mapS::Union{MapS,MapSd,MapS3D}; k::Int = 3)
```

欠損している地図データを埋めます。

**引数:**

  * `mapS`: `MapS`、`MapSd`、または `MapS3D` スカラー磁気異常マップ構造体
  * `k`:    （オプション）k近傍法のための最近傍数

**戻り値:**

  * `mapS`: `MapS`、`MapSd`、または `MapS3D` スカラー磁気異常マップ構造体、埋められたもの
