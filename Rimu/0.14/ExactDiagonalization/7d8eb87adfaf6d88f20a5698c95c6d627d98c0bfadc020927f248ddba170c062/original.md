```
KrylovKitSolver(matrix_free::Bool; kwargs...)
KrylovKitSolver(; matrix_free = false, kwargs...)
```

Algorithm for solving a large [`ExactDiagonalizationProblem`](@ref) to find a few eigenvalues and vectors using the KrylovKit.jl package. The Lanczos method is used for hermitian matrices, and the Arnoldi method is used for non-hermitian matrices.

# Arguments

  * `matrix_free = false`: Whether to use a matrix-free algorithm. If `false`, a sparse matrix   will be instantiated. This is typically faster and recommended for small matrices,   but requires more memory. If `true`, the matrix is not instantiated, which is useful for   large matrices that would not fit into memory. The calculation will parallelise using   threading and MPI if available by making use of [`PDVec`](@ref).
  * `kwargs`: Additional keyword arguments are passed on to the function   [`KrylovKit.eigsolve()`](https://jutho.github.io/KrylovKit.jl/stable/man/eig/#KrylovKit.eigsolve).

See also [`ExactDiagonalizationProblem`](@ref), [`solve`](@ref solve(::ExactDiagonalizationProblem)).

!!! note
    Requires the KrylovKit.jl package to be loaded with `using KrylovKit`.

