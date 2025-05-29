```julia
primitive type Preconditioner <: Enum{Int32} 32
```

Public type used to specify a preconditioner for the linear systems in the solution process.

# Available Options

  * `NONE`:   Dummy option for no preconditioner. In particular used with direct solvers.
  * `JACOBI`:   Preconditioner with diagonal matrix.
  * `ILU`:   Preconditioner with incomplete LU decomposition.
  * `ICHOLESKY`:   Preconditioner with incomplete Cholesky decomposition.
  * `AMG`:   Preconditioner with algebraic multi-grid.
