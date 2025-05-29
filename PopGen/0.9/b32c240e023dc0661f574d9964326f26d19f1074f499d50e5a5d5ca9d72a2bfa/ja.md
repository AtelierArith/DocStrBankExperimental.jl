```
hclust(data::PopData; linkage::Symbol = :single, branchorder::Symbol = :r, distance::PreMetric = euclidean, matrixtype::Symbol = :pca)
```

`Clustering.hclust`（Clustering.jlからの拡張）は、PopDataオブジェクトに対して階層的クラスタリングを実行します。これは、`PopData`オブジェクトをアレル頻度またはPCA行列に変換し、それを距離行列に変換し、その距離行列に対して階層的クラスタリングを実行する便利なメソッドです。多くのメトリックを含む`Hclust`オブジェクトを返しますが、クラスタ割り当ては含まれていません。`cutree(::PopData, ::Hclust; krange...)`を使用して、範囲の`k`クラスタに対するサンプル割り当てを計算します。

**キーワード引数**

  * `linkage`: データポイント間の距離がクラスタ間の距離にどのように集約されるかを定義します（デフォルト: `:single`）

      * `:single`: クラスタメンバー間の最小距離を使用
      * `:average`: クラスタメンバー間の平均距離を使用
      * `:complete`: メンバー間の最大距離を使用
      * `:ward`: 2つのクラスタをマージした後の、ポイントとそのクラスタ重心との平均二乗距離の増加を距離とする
      * `:ward_presquared`: `:ward`と同じですが、距離行列の距離がすでに二乗されていると仮定します。
  * `branchorder`: 葉と枝を順序付けるアルゴリズム（デフォルト: `:r`）

      * `:r`: ノードの高さと元の要素の順序に基づく順序付け（Rのhclustと互換性あり）
      * `:optimal`: 隣接する葉の距離を減少させるように枝を順序付ける「高速最適葉順序付け」[アルゴリズム](https://doi.org/10.1093/bioinformatics/17.suppl_1.S22)
  * `distance`: `matrixtype`に対して計算する距離行列のタイプ（デフォルト: `euclidean`）

      * オプションのリストについては[Distances.jl](https://github.com/JuliaStats/Distances.jl)を参照してください（例: sqeuclideanなど）
  * `matrixtype`: 入力行列のタイプ（デフォルト: `:pca`）

      * `:pca`: 主成分の行列
      * `:freq`: アレル頻度の行列

```
