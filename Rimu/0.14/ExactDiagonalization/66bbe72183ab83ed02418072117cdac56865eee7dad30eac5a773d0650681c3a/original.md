```
LOBPCGSolver(; kwargs...)
```

The Locally Optimal Block Preconditioned Conjugate Gradient Method (LOBPCG). Algorithm for solving an [`ExactDiagonalizationProblem`](@ref) after instantiating a sparse matrix.

LOBPCG is not suitable for non-hermitian eigenvalue problems.

The `kwargs` are passed on to the function [`IterativeSolvers.lobpcg()`](https://iterativesolvers.julialinearalgebra.org/dev/eigenproblems/lobpcg/).

See also [`ExactDiagonalizationProblem`](@ref), [`solve`](@ref solve(::ExactDiagonalizationProblem)).

!!! note
    Requires the IterativeSolvers.jl package to be loaded with `using IterativeSolvers`.

