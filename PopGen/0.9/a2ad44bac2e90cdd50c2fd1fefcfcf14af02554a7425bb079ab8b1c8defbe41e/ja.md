```
fuzzycmeans(data::PopData; c::Int64, fuzziness::Int64 = 2, iterations::Int64 = 100, matrixtype::Symbol = :pca)
```

`Clustering.fuzzy_cmeans`（Clustering.jlから）の拡張で、PopDataオブジェクトに対してFuzzy C-meansクラスタリングを実行します。これは便利なメソッドで、`PopData`オブジェクトをアレル頻度またはPCA行列に変換し、それに対するユークリッド距離行列でFuzzy C-meansクラスタリングを実行します。`FuzzyCMeansResult`オブジェクトを返し、`.weights`フィールドに割り当て重みが含まれます。

**キーワード引数**

  * `c`: 希望するクラスタの数、`Integer`として指定
  * `fuzziness::Integer`: クラスタのファジネス、1より大きくなければならない（デフォルト: `2`）

      * ファジネスが2のものは、クラスタ数が不明なシステムに一般的です
  * `iterations::Int64`: 収束に達するために試みる最大反復回数（デフォルト: `100`）
  * `matrixtype`: 計算する入力行列のタイプ（デフォルト: `:pca`）

      * `:pca`: 主成分の行列
      * `:freq`: スケーリングされたアレル頻度の行列
