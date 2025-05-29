```julia
cluster(::PopData, method::Function ; kwargs)
```

指定された`method`によって`PopData`オブジェクトに対してクラスタリングを実行するための便利なラッパーです（詳細は下記参照）。選択したメソッドには、そのメソッドに適したキーワード引数も提供する必要があります。特定のメソッドに関する詳細は、`?methodname`を使用してそのドキュメント文字列を参照してください。

**クラスタリングメソッド**

  * `kmeans`: K-means++クラスタリング

      * kwargs: `k`, `iterations`, `matrixtype`
  * `kmedoids`: K-medoidsクラスタリング

      * kwargs: `k`, `iterations`, `distance`, `matrixtype`
  * `hclust`: 階層的クラスタリング

      * kwargs: `linkage`, `branchorder`, `distance`, `matrixtype`
  * `fuzzycmeans`: ファジーC-平均クラスタリング

      * kwargs: `c`, `fuzziness`, `iterations`, `matrixtype`
  * `dbscan`: ノイズを伴うアプリケーションのための密度ベースの空間クラスタリング（DBSCAN）

      * kwargs: `radius`, `minpoints`, `distance`, `matrixtype`
