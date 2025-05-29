```
UniformGrid(arch; origin, extent, dims, topology=nothing)
```

Constructs a uniform grid with specified origin, extent, dimensions, and topology.

## Arguments

  * `arch::Architecture`: The associated architecture.
  * `origin::NTuple{N,Number}`: The origin of the grid.
  * `extent::NTuple{N,Number}`: The extent of the grid.
  * `dims::NTuple{N,Integer}`: The dimensions of the grid.
  * `topology=nothing`: The topology of the grid. If not provided, a default `Bounded` topology is used.
