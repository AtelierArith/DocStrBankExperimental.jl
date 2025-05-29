```
function calculateptm(mat; tol=1e-15, heisenberg=true)
function calculateptm(dtype, mat; tol=1e-15, heisenberg=true)
```

Calculate the Pauli Transfer Matrix (PTM) of a matrix `mat`.  The PTM will be real-valued in the Pauli basis. However, it can be complex in a general basis. Pass an optional data type `dtype` when entries are not floats. We truncate small complex components and abs values in the PTM using the `tol` parameter. Note, by default the PTM is calculated in the -> Heisenberg picture <-,  i.e., the PTM is that of the conjugate transpose of the  matrix. This can be changed via the `heisenberg::Bool` keyword argument. Arguments

  * `mat::Matrix`: The evolutioin gate matrix for which the PTM is calculated.
  * `tol::Float64=1e-15`: The tolerance for dropping small values in the PTM.
  * `heisenberg::Bool=true`: Whether the PTM is calculated in the Heisenberg picture.
  * `dtype::DataType`: Default type for a real PTM is `Float64`.

Returns

  * `ptm::Matrix`: The PTM of the conjugate transpose of matrix `mat`.
