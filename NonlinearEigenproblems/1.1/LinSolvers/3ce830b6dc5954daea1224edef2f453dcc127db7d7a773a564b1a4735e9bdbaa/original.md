```
struct ArnoldiEigSolver <: EigSolver
```

A linear eigenproblem solver for large and sparse problems that calls the Arnoldi method implemented in the Julia package ArnoldiMethod.jl.

Constructed as `ArnoldiEigSolver(A, [B,])`, and solves the problem

$$
Ax = λBx
$$

The paramter `B` is optional an default is indentity, for which a standard linear eigenproblem is solved.

See also: [`EigSolver`](@ref) and [`eig_solve`](@ref)
