```
distributed_init_weights_inplace_ops!(asg::SG, fun::F, worker_ids::Vector{Int})
```

(`asg`内のすべての重みを`worker_ids`内のすべてのワーカーで再計算します。インプレース関数`mul!(::RT,::RT)`,`mul!(::RT,::Float64)`,`add!(::RT,::RT)`を定義する必要があります。)

# 引数

  * `asg::SG<:AbstractHierarchicalSparseGrid{N,HCP}}`: 適応型スパースグリッド
  * `fun`::補間される関数。
  * `worker_ids`: 利用可能なすべてのワーカー（`using Distributed; addprocs(...)`を介して追加できます）。
