```julia
abstract type NodePermutation <: ExtendableGrids.AbstractGridIntegerArray1D
```

Key type describing the permutation of the nodes of a partitioned grid with respect  to the unpartitioned origin.

If `pgrid` is the partitioned grid and `grid` is the unpartitioned origin, then 

`pgrid[Coordinates][:,pgrid[NodePermutation]]==grid[Coordinates]`
