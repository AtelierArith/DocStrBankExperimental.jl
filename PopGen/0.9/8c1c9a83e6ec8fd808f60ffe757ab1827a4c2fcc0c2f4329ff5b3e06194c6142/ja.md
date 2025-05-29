```
kmedoids(data::PopData; k::Int64, iterations::Int64 = 100, distance::PreMetric = euclidean, matrixtype::Symbol = :pca)
```

`PopData`オブジェクトに対してKmedoidsクラスタリングを実行します。`KmedoidsResult`オブジェクトを返します。キーワード引数`iterations`（デフォルト: 100）を使用して、収束を達成するために許可される最大反復回数を設定します。内部的には、スケーリングされたアレル頻度の主成分、または単にスケーリングされたアレル頻度自体に対してkmeansクラスタリングが実行されます。どちらの場合も、`missing`値はグローバル平均アレル頻度で置き換えられます。

**キーワード引数**

  * `k`: 希望するクラスタの数、`Integer`として指定
  * `iterations::Int64`: 収束に達するために試みる最大反復回数（デフォルト: `100`）
  * `distance`: `matrixtype`に対して計算する距離行列のタイプ（デフォルト: `euclidean`）

      * オプションのリストについては[Distances.jl](https://github.com/JuliaStats/Distances.jl)を参照してください（例: sqeuclideanなど）
  * `matrixtype`: 計算する入力行列のタイプ（デフォルト: `:pca`）

      * `:pca`: 主成分の行列
      * `:freq`: スケーリングされたアレル頻度の行列
