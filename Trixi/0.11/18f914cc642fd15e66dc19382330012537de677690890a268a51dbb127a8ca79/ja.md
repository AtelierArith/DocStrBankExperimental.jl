```
T8codeMesh(trees_per_dimension; polydeg, mapping=identity,
           RealT=Float64, initial_refinement_level=0, periodicity=true)
```

指定されたサイズの構造化された潜在的に曲がった'T8codeMesh'を作成します。

非周期的境界は':x*neg', ':x*pos', ':y*neg', ':y*pos', ':z*neg', ':z*pos'と呼ばれます。

# 引数

  * 'trees*per*dimension::NTupleE{NDIMS, Int}': 各次元の木の数。
  * 'polydeg::Integer': メッシュの幾何学を格納するために使用される多項式の次数。                     マッピングは、各木の指定された次数の補間多項式によって近似されます。
  * `mapping`: 参照メッシュ（`[-1, 1]^n`）を物理ドメインに変換するための`NDIMS`変数の関数。            `mapping`、`faces`、および`coordinates_min`/`coordinates_max`のいずれか一つのみを使用してください。
  * `faces::NTuple{2*NDIMS}`: ドメインの面を説明する`2 * NDIMS`関数のタプル。                           各関数は`NDIMS-1`引数を取る必要があります。                           `faces[1]`は、単位ハイパーキューブの負のx方向の面がマッピングされる面を説明します。                           単位ハイパーキューブの正のx方向の面は、`faces[2]`で説明される面にマッピングされます。                           `faces[3:4]`は、それぞれ正および負のy方向の面を説明します                           （2Dおよび3Dの場合）。                           `faces[5:6]`は、それぞれ正および負のz方向の面を説明します（3Dの場合）。                           `mapping`、`faces`、および`coordinates_min`/`coordinates_max`のいずれか一つのみを使用してください。
  * `coordinates_min`: 各次元の負の方向のコーナーの座標のベクトルまたはタプル                    長方形メッシュを作成するために。                    `mapping`、`faces`、および`coordinates_min`/`coordinates_max`のいずれか一つのみを使用してください。
  * `coordinates_max`: 各次元の正の方向のコーナーの座標のベクトルまたはタプル                    長方形メッシュを作成するために。                    `mapping`、`faces`、および`coordinates_min`/`coordinates_max`のいずれか一つのみを使用してください。
  * 'RealT::Type': 座標に使用されるべき型。
  * 'initial*refinement*level::Integer': シミュレーション開始前にメッシュを均一にこのレベルまで細分化します。
  * 'periodicity': すべての境界が周期的であるかどうかを決定する'Bool'、または各次元の境界がこの次元で周期的であるかどうかを決定する'NTuple{NDIMS, Bool}'。
