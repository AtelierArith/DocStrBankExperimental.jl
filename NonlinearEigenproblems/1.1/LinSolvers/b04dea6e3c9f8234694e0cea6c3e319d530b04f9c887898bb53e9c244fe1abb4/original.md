```
struct DefaultEigSolver <: EigSolver
```

A linear eigenvalueproblem solver that calls checks for sparsity and accordingly assigns an appropriate solver.

See also: [`EigSolver`](@ref), [`eig_solve`](@ref), [`EigenEigSolver`](@ref), [`ArnoldiEigSolver`](@ref)
