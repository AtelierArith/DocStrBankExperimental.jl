```
eig_solve(solver::EigSolver; [nev,] [target,])
```

This function solves the linear eigenvalue problem represented in `solver::EigSolver`. The `nev` kwarg is controlling the number of eigenvalues aimed for, and `target` specifies around which point the eigenvalues are computed. The former has a defalut value equalt to the seize of the problem, and the latter has a defalut value 0.

Return values are of the form (Vector, Matrix) where the former contains the eigenvalues and the latter the eigenvectors.

This function must be overloaded if a user wants to define their own way of solving linear eigenvalue problems. See [`EigSolver`](@ref) for examples.
