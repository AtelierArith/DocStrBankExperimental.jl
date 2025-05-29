```
struct DeflatedNEPLinSolver <: LinSolver
```

The `DeflatedNEPLinSolver` solves the linear system connected with a deflated NEP. The extended linear system is solveed with a Schur complement strategy, recycling the linear solver of the original NEP. such that

$$
[M, U; X^T, 0][v1; v2] = [b1; b2]
$$

NB1: The implementation assumes minimality index = 1. NB2: The Schur complement is explicitly formed. Hence it is only efficient for a few deflated eigenvalues. See also: [`LinSolver`](@ref), [`DeflatedNEPLinSolverCreator`](@ref), [`deflate_eigpair`](@ref)

# References

  * C. Effenberger, Robust successive computation of eigenpairs for nonlinear eigenvalue problems. SIAM J. Matrix Anal. Appl. 34, 3 (2013), pp. 1231-1256.
