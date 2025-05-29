```
ArpackSolver(; kwargs...)
```

Algorithm for solving an [`ExactDiagonalizationProblem`](@ref) after instantiating a sparse matrix. It uses the Lanzcos method for hermitian problems, and the Arnoldi method for non-hermitian problems, using the Arpack Fortran library. This is faster than [`KrylovKitSolver(; matrix_free=true)`](@ref), but it requires more memory and will only be useful if the matrix fits into memory.

The `kwargs` are passed on to the function [`Arpack.eigs()`](https://arpack.julialinearalgebra.org/stable/eigs/).

See also [`ExactDiagonalizationProblem`](@ref), [`solve`](@ref solve(::ExactDiagonalizationProblem)).

!!! note
    Requires the Arpack.jl package to be loaded with `using Arpack`.

