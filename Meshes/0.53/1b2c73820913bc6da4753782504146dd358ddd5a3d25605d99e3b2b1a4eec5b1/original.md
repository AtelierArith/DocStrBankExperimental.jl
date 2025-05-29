```
GridTopology(dims, [periodic])
```

A data structure for grid topologies with `dims` elements. Optionally, specify which dimensions are `periodic`. Default to aperiodic dimensions.

## Examples

```julia
julia> GridTopology((10,20)) # 10x20 elements in a grid
julia> GridTopology((10,20), (true,false)) # cylinder topology
```
