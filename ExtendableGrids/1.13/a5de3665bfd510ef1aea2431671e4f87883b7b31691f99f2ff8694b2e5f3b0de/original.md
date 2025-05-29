```julia
abstract type PartitionCells <: ExtendableGrids.AbstractGridIntegerArray1D
```

Key type describing the cells of a given partition.

`grid[PartitionCells]` returns an integer vector describing  the cells of a partition  given by its number. Let `pc=grid[PartitionCells]`. Then all cells with index `i ∈ pc[p]:pc[p+1]-1`  belong to partition p.
