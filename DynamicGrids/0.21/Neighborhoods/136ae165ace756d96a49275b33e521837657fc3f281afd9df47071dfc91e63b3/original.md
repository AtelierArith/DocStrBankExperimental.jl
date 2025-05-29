```
Neighborhood
```

Neighborhoods define the pattern of surrounding cells in the "neighborhood" of the current cell. The `neighbors` function returns the surrounding cells as an iterable.

The main kinds of neighborhood are demonstrated below:

![Neighborhoods](https://raw.githubusercontent.com/cesaraustralia/DynamicGrids.jl/media/Neighborhoods.png)

Neighborhoods can be used in `NeighborhoodRule` and `SetNeighborhoodRule` - the same shapes with different purposes. In a `NeighborhoodRule` the neighborhood specifies which cells around the current cell are returned as an iterable from the `neighbors` function. These can be counted, summed, compared, or multiplied with a kernel in an `AbstractKernelNeighborhood`, using [`kernelproduct`](@ref).

In `SetNeighborhoodRule` neighborhoods give the locations of cells around the central cell, as [`offsets`] and absolute [`positions`](@ref) around the index of each neighbor. These can then be written to manually.
