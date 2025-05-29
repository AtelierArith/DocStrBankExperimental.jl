```
P4estMesh(trees_per_dimension; polydeg,
          mapping=nothing, faces=nothing, coordinates_min=nothing, coordinates_max=nothing,
          RealT=Float64, initial_refinement_level=0, periodicity=true, unsaved_changes=true,
          p4est_partition_allow_for_coarsening=true)
```

指定されたサイズの構造化された曲線/高次の `P4estMesh` を作成します。

メッシュを物理ドメインにマッピングする方法は3つあります。

1. ハイパーキューブ `[-1, 1]^n` をマッピングする `mapping` を定義します。
2. 各面をパラメータ化する関数の `Tuple` `faces` を指定します。
3. `coordinates_min` と `coordinates_max` を指定して長方形のメッシュを作成します。

非周期境界は `:x_neg`, `:x_pos`, `:y_neg`, `:y_pos`, `:z_neg`, `:z_pos` と呼ばれます。

# 引数

  * `trees_per_dimension::NTupleE{NDIMS, Int}`: 各次元の木の数。
  * `polydeg::Integer`: メッシュの幾何学を格納するために使用される多項式の次数。                     マッピングは、各木の指定された次数の補間多項式によって近似されます。
  * `mapping`: 参照メッシュ (`[-1, 1]^n`) を物理ドメインに変換するマッピングを記述する `NDIMS` 変数の関数。            `mapping`、`faces`、および `coordinates_min`/`coordinates_max` のいずれか一つのみを使用してください。
  * `faces::NTuple{2*NDIMS}`: ドメインの面を記述する `2 * NDIMS` 関数のタプル。                           各関数は `NDIMS-1` 引数を取る必要があります。                           `faces[1]` は、単位ハイパーキューブの負の x 方向の面がマッピングされる面を記述します。                           単位ハイパーキューブの正の x 方向の面は、`faces[2]` で記述された面にマッピングされます。                           `faces[3:4]` はそれぞれ正の y 方向と負の y 方向の面を記述します                           （2D および 3D）。                           `faces[5:6]` はそれぞれ正の z 方向と負の z 方向の面を記述します（3D）。                           `mapping`、`faces`、および `coordinates_min`/`coordinates_max` のいずれか一つのみを使用してください。
  * `coordinates_min`: 長方形のメッシュを作成するために、各次元の負の方向のコーナーの座標のベクトルまたはタプル。                    `mapping`、`faces`、および `coordinates_min`/`coordinates_max` のいずれか一つのみを使用してください。
  * `coordinates_max`: 長方形のメッシュを作成するために、各次元の正の方向のコーナーの座標のベクトルまたはタプル。                    `mapping`、`faces`、および `coordinates_min`/`coordinates_max` のいずれか一つのみを使用してください。
  * `RealT::Type`: 座標に使用されるべき型。
  * `initial_refinement_level::Integer`: シミュレーション開始前にメッシュを均一にこのレベルまで細分化します。
  * `periodicity`: すべての境界が周期的であるかどうかを決定する `Bool` か、                各次元の境界がこの次元で周期的であるかどうかを決定する `NTuple{NDIMS, Bool}`。
  * `unsaved_changes::Bool`: `true` に設定すると、メッシュはメッシュファイルに保存されます。
  * `p4est_partition_allow_for_coarsening::Bool`: メッシュ適応性をドメインのパーティショニングから独立させるために、AMRを使用する際は `true` である必要があります。静的メッシュの場合は、より細かいパーティショニングを許可するために `false` であるべきです。
