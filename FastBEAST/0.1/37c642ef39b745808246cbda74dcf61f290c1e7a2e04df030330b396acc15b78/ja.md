```
KMeansTreeOptions <: TreeOptions
```

は、[`create_tree`](@ref) 関数が作成するツリーを説明するデータ型です。

# フィールド

  * `iterations`: 各レベルでの反復回数、デフォルトは1回の反復
  * `nchildren`: 各ノードの子の数を定義します。デフォルトは2
  * `nmin`: クラスタ内で分割されるために必要なデータポイントの最小数を定義します。デフォルトは1
  * `maxlevel`: 最大レベル数を定義します。デフォルトは100。
  * `algorithm`: 使用されるアルゴリズムを定義します。:naive アプローチは推奨されません。デフォルトはラップされた ParallelKMeans アルゴリズムです。
