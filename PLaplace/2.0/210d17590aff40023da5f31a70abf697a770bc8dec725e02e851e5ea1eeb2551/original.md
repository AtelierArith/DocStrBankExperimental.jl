```julia
primitive type LinearSolver <: Enum{Int32} 32
```

Public type used to specify the linear solver in the solution algorithm.

# Available Options

  * `LU`:   Direct solver with LU decomposition.
  * `CHOLESKY`:   Direct solver with Cholesky decomposition.   Default options since Hessian is supposed to be symmetric positive definite.
  * `CG`:   Iterative solver using the conjugate gradients methods.
  * `BICGSTAB`:   Iterative solver using the bi-conjugate gradients stabilized method.
  * `GMRES`:   Iterative solver using the generalized minimal residual method.   Has proven convergence for unsymmetric systems, but requires a lot of memory.
