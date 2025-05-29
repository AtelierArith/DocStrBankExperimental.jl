```
init_weights!(asg::SG, cpts::AbstractVector{HCP}, fun::F)
```

(`cpts`内の)すべての重みを再計算します。

# 引数

  * `asg::SG<:AbstractHierarchicalSparseGrid{N,HCP}}`: 適応的スパースグリッド
  * `cpts::AbstractVector{HCP}`: `cpts`内のすべてのコレクションポイントの重みが(再)計算されます。
  * `fun`::補間される関数。
