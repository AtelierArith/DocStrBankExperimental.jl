```
diagonalize(op::DataOperator[, routine; params...])
```

Finds eigenvalues and eigenvectors for a `Operator` and stores them in an `Eigensystem`.

Two routines are available:

  * `:lapack` uses the `eigen` function from the standard `LinearAlgebra` package.
  * `:krylovkit` uses the Lanczos algorithm from the `KrylovKit` package.   Accepts following parameters:

      * `v0` is the starting vector. Default is `rand(ComplexF64, size(op.data, 1))`.
      * `n` is the target number of eigenvectors. Default is 10.

    All other keyword arguments are passed to the `KrylovKit.eigsolve` function. See its documentation for details.
  * `:auto` automatically selects the routine based on the size of the operator.

The default routine is `:lapack` for dense operators. If the operator matrix is less than 5000×5000, it is automatically converted to a dense operator. In other cases `:krylovkit` is used.

## Example

```jldoctest
julia> using LatticeModels

julia> l = SquareLattice(4, 4);

julia> H = tightbinding_hamiltonian(l)
Hamiltonian(dim=16x16)
System: One particle on 16-site SquareLattice in 2D space
16×16 SparseArrays.SparseMatrixCSC{ComplexF64, Int64} with 48 stored entries:
⎡⠪⡢⠑⢄⠀⠀⠀⠀⎤
⎢⠑⢄⠪⡢⠑⢄⠀⠀⎥
⎢⠀⠀⠑⢄⠪⡢⠑⢄⎥
⎣⠀⠀⠀⠀⠑⢄⠪⡢⎦

julia> eig = diagonalize(H)
Diagonalized Hamiltonian (16 eigenvectors)
Eigenvalues in range -3.23607 .. 3.23607
System: One particle on 16-site SquareLattice in 2D space
```
