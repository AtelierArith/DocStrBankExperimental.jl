```
klu(A::SparseMatrixCSC) -> K::KLUFactorization
klu(n, colptr::Vector{Ti}, rowval::Vector{Ti}, nzval::Vector{Tv}) -> K::KLUFactorization
```

Compute the LU factorization of a sparse matrix `A` using KLU[^ACM907].

For sparse `A` with real or complex element type, the return type of `K` is `KLUFactorization{Tv, Ti}`, with `Tv` = `Float64` or `ComplexF64` respectively and `Ti` is an integer type (`Int32` or `Int64`).

The individual components of the factorization `K` can be accessed by indexing:

| Component | Description                                                      |
|:--------- |:---------------------------------------------------------------- |
| `L`       | `L` (lower triangular) part of `LU` of the diagonal blocks       |
| `U`       | `U` (upper triangular) part of `LU` of the diagonal blocks       |
| `F`       | `F` (upper triangular) part of `LU + F`, the off-diagonal blocks |
| `p`       | right permutation `Vector`                                       |
| `q`       | left permutation `Vector`                                        |
| `Rs`      | `Vector` of scaling factors                                      |

The relation between `K` and `A` is

`K.L * K.U + K.F  == K.Rs` \ `A[K.p, K.q]`

`K` further supports the following functions:

  * `LinearAlgebra.\`

# Arguments

  * `A::SparseMatrixCSC` or `n::Integer`, `colptr::Vector{Ti}`, `rowval::Vector{Ti}`, `nzval::Vector{Tv}`: The sparse matrix or the zero-based sparse matrix components to be factored.
  * `check::Bool`: If `true` (default) check for errors after the factorization. If `false` errors must be checked by the user with `klu.common.status`.
  * `allowsingular::Bool`: If `true` (default `false`) allow the factorization to proceed even if the matrix is singular. Note that this will allow for

silent divide by zero errors in subsequent `solve!` or `ldiv!` calls if singularity is not checked by the user with `klu.common.status == KLU.KLU_SINGULAR`

!!! note
    `klu(A::SparseMatrixCSC)` uses the KLU[^ACM907] library that is part of SuiteSparse. As this library only supports sparse matrices with [`Float64`](@ref) or `ComplexF64` elements, `lu` converts `A` into a copy that is of type `SparseMatrixCSC{Float64}` or `SparseMatrixCSC{ComplexF64}` as appropriate.


[^ACM907]: Davis, Timothy A., & Palamadai Natarajan, E. (2010). Algorithm 907: KLU, A Direct Sparse Solver for Circuit Simulation Problems. ACM Trans. Math. Softw., 37(3). doi:10.1145/1824801.1824814
