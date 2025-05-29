```
NodePair
```

`NodePair` is a wrapper for vector-valued data that lie at the nodes of dual cells and primal cells. `NodePair` type data have fields `u` and `v` for the components of the vector field. These are the normal components of a vector field on nodes that form the faces of a virtual cell centered at one of the faces of the primal cell.

# Constructors

  * `NodePair(C,dims)` creates a vector field of zeros in cells of type `C` (where `C` is either `Dual` or `Primal`), on a grid of dimensions `dims`. Note that `dims` represent the number of dual cells on the grid.
  * `NodePair(C,w)` performs the same construction, but uses existing field data `w` of `GridData` type to determine the size of the grid.
  * Adding the `dtype=` keyword allows the data type of the field data to be changed. The default is `Float64`, but can be changed to, e.g., `ComplexF64`
