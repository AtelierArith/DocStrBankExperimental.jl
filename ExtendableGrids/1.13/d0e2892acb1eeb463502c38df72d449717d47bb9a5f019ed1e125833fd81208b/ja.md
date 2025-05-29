```julia
abstract type PartitionEdges <: ExtendableGrids.AbstractGridIntegerArray1D
```

与えられたパーティションのエッジを記述するキータイプです。

`grid[PartitionEdges]` は、番号によって与えられたパーティションのエッジを記述する整数ベクトルを返します。`pe=grid[PartitionEdges]` とします。すると、すべてのエッジでインデックス `i ∈ pe[p]:pe[p+1]-1` はパーティション p に属します。
