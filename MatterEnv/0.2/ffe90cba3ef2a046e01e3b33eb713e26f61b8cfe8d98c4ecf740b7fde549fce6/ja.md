```
distinguish_spin(projection_all::Projection,
    projection_axis::Projection,
    bands::Bands)
```

スピンアップとスピンダウンの投影を区別します。（PROCARから読み込まれた投影で使用）

# 引数

  * `projection_all::Projection`: 総投影磁化
  * `projection_axis::Projection`: x、y、またはz軸における投影磁化
  * `bands::Bands`: バンドのメタデータ

# 戻り値

  * `ProjectionWithSpin`: スピンアップとスピンダウンの投影
  * `BandsWithSpin`: スピンアップとスピンダウンのバンドのメタデータ
