```
     partition(grid::ExtendableGrid,
               alg::AbstractPartitioningAlgorithm;
               nodes = false,
               keep_nodepermutation = false,
               edges = false )
```

Partition cells of `grid` according to `alg`, such that the neighborhood graph of partitions is colored in such a way, that all partitions with  a given color can be worked on in parallel.  Cells are renumbered such that cell numbers for a given partition are numbered contiguously. 

Return the resulting grid.

Useful for parallel FEM assembly and cellwise FVM assembly.

Keyword arguments:

  * `nodes`: if true, induce node partitioning from cell partitioning. Used for node/edgewise FVM assembly.  In addition the resulting partitioning supports parallel matrix-vector products with `SparseMatrixCSC`. Nodes are renumbered compared to the original grid. If `false` (default), a trivial partitioning of the  nodes is created such that all nodes belong to partition 1 and all others are empty.
  * `keep_nodepermutation`: if true, keep the node permutation with respect to the original grid in `grid[`[`NodePermutation`](@ref)`]`.
  * `edges`: if true, induce partitioning of edges from cell partitioning. Used for node/edgewise FVM assembly.  This step creates a number of relatively expensive additional adjacencies.  If `false` (default), a trivial partitioning of the   edges is created such that all edges belong to partition 1 and all others are empty.

Access:

  * [`pcolors`](@ref) returns the range of partition colors
  * [`pcolor_partitions`](@ref)  returns the range of partition numbers for a given color
  * [`partition_cells`](@ref) provides the range of cell numbers of a given partition
  * [`partition_nodes`](@ref) provides the range of node numbers of a given partition
  * [`partition_edges`](@ref) provides the range of edge numbers of a given partition

A parallel loop over grid cells thus looks like

```julia
for color in pcolors(grid)
    @threads for part in pcolor_partitions(grid, color)
                for cell in partition_cells(grid, part)
                 ...
                end
             end
end
```

Without a call to `partition`, all these functions return trivial data such that the above sample code stays valid.

!!! note
    `partition` must be called before obtaining any other adjacencies of a grid.


Currently, partitioning does not cover the boundary, boundary cells belong to one big trivial partition.
