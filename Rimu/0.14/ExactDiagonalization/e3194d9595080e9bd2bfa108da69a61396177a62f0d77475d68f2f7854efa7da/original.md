```
LinearAlgebraSolver(; kwargs...)
```

Algorithm for solving an [`ExactDiagonalizationProblem`](@ref) using the dense-matrix eigensolver from the `LinearAlgebra` standard library. This is only suitable for small matrices.

The `kwargs` are passed on to function [`LinearAlgebra.eigen`](https://docs.julialang.org/en/v1/stdlib/LinearAlgebra/#LinearAlgebra.eigen).

# Keyword arguments

  * `permute = true`: Whether to permute the matrix before diagonalization.
  * `scale = true`: Whether to scale the matrix before diagonalization.
  * `sortby`: The sorting order for the eigenvalues.

See also [`ExactDiagonalizationProblem`](@ref), [`solve`](@ref solve(::ExactDiagonalizationProblem)).
