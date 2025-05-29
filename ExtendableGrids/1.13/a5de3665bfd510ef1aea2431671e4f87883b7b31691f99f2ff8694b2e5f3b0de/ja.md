```julia
abstract type PartitionCells <: ExtendableGrids.AbstractGridIntegerArray1D
```

与えられたパーティションのセルを記述するキータイプ。

`grid[PartitionCells]` は、番号によって与えられたパーティションのセルを記述する整数ベクトルを返します。`pc=grid[PartitionCells]` とします。すると、すべてのセルでインデックス `i ∈ pc[p]:pc[p+1]-1` はパーティション p に属します。
