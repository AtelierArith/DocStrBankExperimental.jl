```julia
abstract type PColorPartitions <: ExtendableGrids.AbstractGridIntegerArray1D
```

Key type describing colors of partitions. These correspond to  a coloring of the neighborhood graphs of partitions such that  operations (e.g. FEM assembly) on partitions of a given color can  be performed in parallel.

`grid[PColorPartitions]` returns an integer vector describing  the partition colors ("pcolors") of a grid.  Let `p=grid[PColorPartitions]`. Then all partitions with numbers `i ∈ p[c]:p[c+1]-1`  have "color" `c`. See also [`pcolors`](@ref).
