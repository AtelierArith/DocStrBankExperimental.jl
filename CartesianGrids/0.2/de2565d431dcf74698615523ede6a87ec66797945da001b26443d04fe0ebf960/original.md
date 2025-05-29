```
CartesianGrids.YEdges
```

`CartesianGrids.YEdges` is a wrapper for scalar-valued data that lie at the centers of either dual cells or primary cells. A `CartesianGrids.YEdges` type can be accessed by indexing like any other array, and allows the use of `size`, `similar`, `zero` functions.

# Constructors

  * `CartesianGrids.YEdges(C,dims)` creates a field of zeros in cells of type `C` (where `C` is either `Dual` or `Primal`), on a grid of dimensions `dims` (a tuple). Note that `dims` represent the number of dual cells on the grid, even if `C` is `Primal`.
  * `CartesianGrids.YEdges(C,w)` performs the same construction, but uses existing field data `w` of `GridData` type to determine the size of the grid.
  * Adding the `dtype=` keyword allows the data type of the field data to be changed. The default is `Float64`, but can be changed to, e.g., `ComplexF64`
