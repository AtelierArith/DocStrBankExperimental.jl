```
partition!(forest; kw...)
```

Partition the quadrants of the forest.  By default this will partition the quadrants equally across the ranks of the forest.

By default sibling elements are split among the ranks.  This means they cannot be coarsened with `coarsen!` and can cause MPI dependent coarsening. If `allow_for_coarsening==true` then this is avoided by keeping sibling quadrants on the same rank.

A `weight(forest, treeid, quadrant)` callback may provided (which gives the `Float64` weight of each quadrant) for a weighted partitioning of the forest.

Alternatively, the forest may be partitioned to equally distribute the globally numbered nodes via [`LNodes`](@ref).  This is done by setting `lnodes_degree` to the node degree.  This requires the [`GhostLayer`](@ref) which if not passed in `ghost` will be created.

The keyword arguments (`kw...`) for the partitioning are:

  * `ghost = nothing`: [`GhostLayer`](@ref) used when partitioning by [`LNodes`](@ref).
  * `lnodes_degree = nothing`: partition based on [`LNodes`](@ref) if this is set to the degree.
  * `allow_for_coarsening = false`: if `true` sibling groups that may be coarsened will be collect on the same rank.
  * `weight = nothing`: callback that give the `Float64` weight of each quadrant to perform a weighted partitioning.

See `@doc P4estTypes.P4est.p4est_partition_ext`, `@doc P4estTypes.P4est.p8est_partition_ext`, `@doc P4estTypes.P4est.p4est_partition_lnodes`, and `@doc P4estTypes.P4est.p8est_partition_lnodes`, for more information about the underlying p4est partition functions.
