```
StructuredMesh(cells_per_dimension, faces; 
               RealT = Float64,
               periodicity = true)
```

指定されたサイズと形状のStructuredMeshを作成し、`RealT`を座標タイプとして使用します。

# 引数

  * `cells_per_dimension::NTupleE{NDIMS, Int}`: 各次元のセルの数。
  * `faces::NTuple{2*NDIMS}`: ドメインの面を記述する`2 * NDIMS`関数のタプル。                           各関数は`NDIMS-1`の引数を取る必要があります。                           `faces[1]`は、単位ハイパーキューブの負のx方向の面がマッピングされる面を記述します。                           単位ハイパーキューブの正のx方向の面は、`faces[2]`で記述された面にマッピングされます。                           `faces[3:4]`は、それぞれ正のy方向と負のy方向の面を記述します（2Dおよび3Dの場合）。                           `faces[5:6]`は、それぞれ正のz方向と負のz方向の面を記述します（3Dの場合）。
  * `RealT::Type`: 座標に使用するタイプ。
  * `periodicity`: すべての境界が周期的であるかどうかを決定する`Bool`、または各次元の境界がこの次元で周期的であるかどうかを決定する`NTuple{NDIMS, Bool}`。
