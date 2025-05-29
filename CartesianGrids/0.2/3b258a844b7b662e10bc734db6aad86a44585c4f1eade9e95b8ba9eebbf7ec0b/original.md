```
Edges
```

`Edges` is a wrapper for vector-valued data that lie at the faces of either dual cells or primary cells. `Edges` type data have fields `u` and `v` for the components of the vector field. These are the normal components of the vector field on the vertical and horizontal faces of the corresponding cell.

# Constructors

  * `Edges(C,dims)` creates a vector field of zeros in cells of type `C` (where `C` is either `Dual` or `Primal`), on a grid of dimensions `dims`. Note that `dims` represent the number of dual cells on the grid.
  * `Edges(C,w)` performs the same construction, but uses existing field data `w` of `GridData` type to determine the size of the grid.
  * Adding the `dtype=` keyword allows the data type of the field data to be changed. The default is `Float64`, but can be changed to, e.g., `ComplexF64`
