```julia
abstract type PartitionNodes <: ExtendableGrids.AbstractGridIntegerArray1D
```

Key type describing the nodes of a given partition.

`grid[PartitionNodes]` returns an integer vector describing  the nodes of a partition  given by its number. Let `pn=grid[PartitionNodes]`. Then all nodes with index `i ∈ pn[p]:pn[p+1]-1`  belong to partition p.
