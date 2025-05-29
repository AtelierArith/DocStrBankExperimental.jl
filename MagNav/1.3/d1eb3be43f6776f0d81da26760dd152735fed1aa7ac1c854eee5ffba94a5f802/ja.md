```
map_fill!(mapS::Union{MapS,MapSd,MapS3D}; k::Int = 3)
```

欠損しているマップデータを埋める。

**引数:**

  * `mapS`: `MapS`、`MapSd`、または `MapS3D` スカラー磁気異常マップ構造体
  * `k`:    （オプション）k近傍法のための最近傍数

**戻り値:**

  * `nothing`: `mapS` 内の `map` フィールドが埋められたマップデータで変更される
