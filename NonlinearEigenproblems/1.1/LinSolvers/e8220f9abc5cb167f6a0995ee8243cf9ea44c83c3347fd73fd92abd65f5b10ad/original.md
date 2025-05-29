```
struct EigenEigSolver <: EigSolver
```

A linear eigenvalueproblem solver that calls Julia's in-built eigen()

Constructed as `EigenEigSolver(A, [B,])`, and solves the problem

$$
Ax = λBx
$$

The paramter `B` is optional an default is indentity, for which a standard linear eigenproblem is solved.

See also: [`EigSolver`](@ref) and [`eig_solve`](@ref)
