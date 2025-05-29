```
NCMSolver
```

Common interface for solving NCM problems. Algorithm-specific cache is stored in the `cacheval` field.

  * `A`: The input matrix. Must be square. Should be symmetric.
  * `p`: The parameters for the problem. Defaults to `NullParameters`. Currently unused.
  * `alg`: The algorithm used by the solver.
  * `cacheval`: Algorithm-specific cache.
  * `isfresh`: `true` if the cacheval hasn't been set yet.
  * `abstol`: The absolute tolerance. Defaults to `√(eps(eltype(A)))`.
  * `reltol`: The relative tolerance. Defaults to `√(eps(eltype(A)))`.
  * `maxiters`: The number of iterations allowed. Defaults to `size(A,1)`
  * `ensure_pd`: Checks (and corrects) that the resulting matrix is positive definite. Defaults to `false`.
  * `verbose`: Whether to print extra information. Defaults to `false`.
