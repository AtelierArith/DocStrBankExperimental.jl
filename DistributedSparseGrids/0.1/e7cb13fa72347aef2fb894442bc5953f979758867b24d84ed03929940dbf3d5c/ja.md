```
distributed_init_weights!(asg::SG, fun::F, worker_ids::Vector{Int})
```

`asg`内のすべての重みを`worker_ids`内のすべてのワーカーで計算します。

# 引数

  * `asg::SG<:AbstractHierarchicalSparseGrid{N,HCP}}`: 適応スパースグリッド
  * `fun`::補間される関数。
  * `worker_ids`: 利用可能なすべてのワーカー（`using Distributed; addprocs(...)`を介して追加できます）。
