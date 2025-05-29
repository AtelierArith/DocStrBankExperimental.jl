```
StructuredMesh(cells_per_dimension, coordinates_min, coordinates_max;
               periodicity = true)
```

非曲面構造メッシュを表すStructuredMeshを作成します。領域は長方形です。

# 引数

  * `cells_per_dimension::NTuple{NDIMS, Int}`: 各次元のセルの数。
  * `coordinates_min::NTuple{NDIMS, RealT}`: 各次元の負の方向のコーナーの座標。
  * `coordinates_max::NTuple{NDIMS, RealT}`: 各次元の正の方向のコーナーの座標。
  * `periodicity`: すべての境界が周期的であるかどうかを決定する`Bool`、または各次元の境界がこの次元で周期的であるかどうかを決定する`NTuple{NDIMS, Bool}`。
