```julia
abstract type PartitionEdges <: ExtendableGrids.AbstractGridIntegerArray1D
```

Key type describing the edges of a given partition.

`grid[PartitionEdges]` returns an integer vector describing  the edges of a partition  given by its number. Let `pe=grid[PartitionEdges]`. Then all edges with index `i ∈ pe[p]:pe[p+1]-1`  belong to partition p.
