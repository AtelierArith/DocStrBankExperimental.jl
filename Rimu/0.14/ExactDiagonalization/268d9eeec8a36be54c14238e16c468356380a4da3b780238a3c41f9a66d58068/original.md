```
solve(p::ExactDiagonalizationProblem, [algorithm]; kwargs...)
```

Solve an [`ExactDiagonalizationProblem`](@ref) `p` directly. Optionally specify an `algorithm.` Returns a result type with the eigenvalues, eigenvectors, and convergence information.

For a description of the keyword arguments, see the documentation for [`ExactDiagonalizationProblem`](@ref).

See also [`solve(::ProjectorMonteCarloProblem)`](@ref CommonSolve.solve(::ProjectorMonteCarloProblem)).
