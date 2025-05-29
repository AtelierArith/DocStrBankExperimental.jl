```
GeneralizedRandomTessellatedStratified
```

`GeneralizedRandomTessellatedStratified` is a type of [`BONSampler`](@ref) for generating [`BiodiversityObservationNetwork`](@ref)s with spatial spreading.

*Arguments*:

  * `number_of_nodes`: the number of sites to select
  * `grid_size`: if being used on a polygon, the dimensions of the grid used to cover the extent. GRTS sampling uses discrete Cartesian indices

@Olsen

GRTS represents each cell of a rasterized version of the sampling domain using an address, where the address of each cell is represented as a `D`-digit base-4 number. 

The value of `D` depends on the size of the raster. GRTS works by recursively splitting the rasterized domain into quadrants, and those quadrants into further quadrants, until a single pixel is reached. At each step, each quadrant is randomly labeled with a number 1, 2, 3, or 4 (without replacement, so all values are used). 

The addresses are then sorted numerically, and the `number_of_nodes` smallest values are chosen.
