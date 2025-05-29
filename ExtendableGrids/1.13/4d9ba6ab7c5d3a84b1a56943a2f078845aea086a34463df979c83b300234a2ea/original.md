```julia
abstract type PartitionBFaces <: ExtendableGrids.AbstractGridIntegerArray1D
```

Key type describing the boundary faces of a given partition.

`grid[PartitionBFaces]` returns an integer vector describing  the boundary faces of a partition  given by its number. Let `pc=grid[PartitionCells]`. Then all cells with index `i ∈ pc[p]:pc[p+1]-1`  belong to partition p.
