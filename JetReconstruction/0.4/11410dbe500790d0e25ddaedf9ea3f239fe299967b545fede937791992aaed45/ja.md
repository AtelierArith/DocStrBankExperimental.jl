```
n_exclusive_jets(clusterseq::ClusterSequence; dcut::AbstractFloat)
```

クラスタリング履歴を含むClusterSequenceの排他的なジェットの数を、特定のdcut値を超えるものとして返します。

# 引数

  * `clusterseq::ClusterSequence`: クラスタリング履歴を含む`ClusterSequence`オブジェクト。
  * `dcut::AbstractFloat`: 再構成における距離パラメータの最大値。

# 戻り値

`ClusterSequence`オブジェクト内の排他的なジェットの数。

# 例

```julia
n_exclusive_jets(clusterseq, dcut = 20.0)
```
