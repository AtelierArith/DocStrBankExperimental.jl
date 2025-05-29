```julia
abstract type PartitionNodes <: ExtendableGrids.AbstractGridIntegerArray1D
```

与えられたパーティションのノードを記述するキータイプ。

`grid[PartitionNodes]` は、番号によって与えられたパーティションのノードを記述する整数ベクトルを返します。`pn=grid[PartitionNodes]` とします。すると、すべてのノードはインデックス `i ∈ pn[p]:pn[p+1]-1` に属し、パーティション p に属します。
