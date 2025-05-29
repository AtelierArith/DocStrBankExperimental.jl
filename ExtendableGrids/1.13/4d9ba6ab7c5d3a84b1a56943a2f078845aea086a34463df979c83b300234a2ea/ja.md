```julia
abstract type PartitionBFaces <: ExtendableGrids.AbstractGridIntegerArray1D
```

与えられたパーティションの境界面を記述するキータイプ。

`grid[PartitionBFaces]` は、番号で与えられたパーティションの境界面を記述する整数ベクトルを返します。`pc=grid[PartitionCells]` とします。すると、すべてのセルでインデックス `i ∈ pc[p]:pc[p+1]-1` はパーティション p に属します。
