```
MatrixHamiltonian(
    mat::AbstractMatrix{T};
    starting_address::Int = starting_address(mat)
) <: AbstractHamiltonian{T}
```

Wrap an abstract matrix `mat` as an [`AbstractHamiltonian`](@ref) object. Works with stochastic methods of [`ProjectorMonteCarloProblem()`](@ref) and [`DVec`](@ref). Optionally, a valid index can be provided as the [`starting_address`](@ref).

Specialised methods are implemented for sparse matrices of type `AbstractSparseMatrixCSC`. One based indexing is required for the matrix `mat`.
