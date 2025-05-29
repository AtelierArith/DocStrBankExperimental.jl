```
MultiRegionGrid(global_grid; partition = XPartition(2),
                             devices = nothing,
                             validate = true)
```

Split a `global_grid` into different regions handled by `devices`.

# Positional Arguments

  * `global_grid`: the grid to be divided into regions.

# Keyword Arguments

  * `partition`: the partitioning required. The implemented partitioning are `XPartition`              (division along the $x$ direction) and `YPartition` (division along              the $y$ direction).
  * `devices`: the devices to allocate memory on. If `nothing` is provided (default) then memorey is            allocated on the the `CPU`. For `GPU` computation it is possible to specify the total            number of GPUs or the specific GPUs to allocate memory on. The number of devices does            not need to match the number of regions.
  * `validate :: Boolean`: Whether to validate `devices`; defautl: `true`.

# Example

```@example multiregion
julia> using Oceananigans

julia> using Oceananigans.MultiRegion: MultiRegionGrid, XPartition

julia> grid = RectilinearGrid(size=(12, 12), extent=(1, 1), topology=(Bounded, Bounded, Flat));

julia> multi_region_grid = MultiRegionGrid(grid, partition = XPartition(4))
```
