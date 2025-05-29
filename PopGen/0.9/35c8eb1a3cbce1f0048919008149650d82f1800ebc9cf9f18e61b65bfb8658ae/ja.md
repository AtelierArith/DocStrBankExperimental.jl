```
dbscan(::PopData; radius::Float64, minpoints::Int64 = 2, distance::PreMetric = euclidean, matrixtype::Symbol = :pca)
```

`Clustering.dbscan`（Clustering.jlから）の拡張で、PopDataオブジェクトに対してノイズを伴う密度ベースの空間クラスタリング（DBSCAN）を実行します。これは、`PopData`オブジェクトをアレル頻度またはPCA行列に変換し、その距離行列に対してDBSCANクラスタリングを実行する便利なメソッドです。`DbscanResult`オブジェクトを返し、`.assignments`フィールドに割り当てが含まれます。

**キーワード引数**

  * `radius::Float64`: 点の近傍の半径
  * `minpoints::Int`: コアポイントの近傍の最小数（デフォルト: `2`）
  * `distance`: `matrixtype`に対して計算する距離行列のタイプ（デフォルト: `euclidean`）

      * オプションのリストについては[Distances.jl](https://github.com/JuliaStats/Distances.jl)を参照してください（例: sqeuclideanなど）
  * `matrixtype`: 入力行列のタイプ（デフォルト: `:pca`）

      * `:pca`: 主成分の行列
      * `:freq`: アレル頻度の行列
