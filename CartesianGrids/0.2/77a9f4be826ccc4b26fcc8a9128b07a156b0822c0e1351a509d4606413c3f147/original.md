```
EdgeGradient
```

`EdgeGradient` is a wrapper for tensor-valued data that lie partly at the nodes of dual cells and primary cells. `EdgeGradient` type data have fields `dudx`, `dudy`, `dvdx`, `dvdy` for the components of the tensor field. The diagonal components lie at one set of nodes (e.g. Primal), and the offdiagonal at the other set (e.g. Dual).

# Constructors

  * `EdgeGradient(C,dims)` creates a tensor field of zeros in cells of type `C` (where `C` is either `Dual` or `Primal`), on a grid of dimensions `dims`. Note that `dims` represent the number of dual cells on the grid.
  * `EdgeGradient(C,w)` performs the same construction, but uses existing field data `w` of `GridData` type to determine the size of the grid.
  * Adding the `dtype=` keyword allows the data type of the field data to be changed. The default is `Float64`, but can be changed to, e.g., `ComplexF64`
