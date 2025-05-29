```
init_weights!(asg::SG, fun::F)
```

（再）計算すべての重みを `asg` において。

# 引数

  * `asg::SG<:AbstractHierarchicalSparseGrid{N,HCP}}`: 適応的スパースグリッド
  * `fun`::補間される関数。
