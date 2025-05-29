```
DeflatedNEPLinSolverCreator(orglinsolvercreator)
```

This is the creator for case of a deflated NEP. The argument `orglinsolvercreator` is the `LinSolverCreator` for the original NEP. The extended linear system

$$
[M, U; X^T, 0][v1; v2] = [b1; b2]
$$

is solved with a Schur complement strategy, recycling the linear solver of the original NEP. Hence, pre-computed entities such as, e.g., factorizations and preconditioners can be reused.

NB1: The implementation assumes minimality index = 1. NB2: The Schur complement is explicitly formed. Hence it is only efficient for a few deflated eigenvalues.

See also: [`DeflatedNEPLinSolver`](@ref), [`create_linsolver`](@ref), [`deflate_eigpair`](@ref)

# References

  * C. Effenberger, Robust successive computation of eigenpairs for nonlinear eigenvalue problems. SIAM J. Matrix Anal. Appl. 34, 3 (2013), pp. 1231-1256.
