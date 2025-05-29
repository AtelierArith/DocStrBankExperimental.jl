```
distributed_init_weights!(asg::SG, cpts::AbstractVector{HCP}, fun::F, worker_ids::Vector{Int})
```

`worker_ids`のすべてのワーカーで`cpts`のすべての重みを計算します。

# 引数

  * `asg::SG<:AbstractHierarchicalSparseGrid{N,HCP}}`: 適応型スパースグリッド
  * `cpts::AbstractVector{HCP}`: `cpts`のコレクションポイントのすべての重みが（再）計算されます。
  * `fun`::補間される関数。
  * `worker_ids`: 利用可能なすべてのワーカー（`using Distributed; addprocs(...)`を介して追加できます）。
