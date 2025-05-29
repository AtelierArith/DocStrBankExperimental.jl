```
partition_from_color(ranks,global_to_color;multicast=false,source=MAIN)
```

Build an arbitrary 1d partition by defining the parts via the argument `global_to_color` (see below). The output is a vector of vectors containing the indices in each component of the partition. The `eltype` of the result implements the [`AbstractLocalIndices`](@ref) interface.

# Arguments

  * `ranks`: Array containing the distribution of ranks.
  * `global_to_color`: If `multicast==false`,  `global_to_color[gid]` contains the part id that owns the global id `gid`. If `multicast==true`, then   `global_to_color[source][gid]` contains the part id that owns the global id `gid`.

# Key-word arguments

  * `multicast=false`
  * `source=MAIN`

This function is useful when generating a partition using a graph partitioner such as METIS. The argument `global_to_color` is the usual output of such tools.
