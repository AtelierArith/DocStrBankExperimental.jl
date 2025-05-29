KINSOL: Newton-Krylov technique solver

```julia
KINSOL(;
    linear_solver = :Dense,
    jac_upper = 0,
    jac_lower = 0,
    userdata = nothing,
    prec_side = 0,
    krylov_dim = 0,
    globalization_strategy = :None
    maxsetupcalls=0
)
```

The choices for the linear solver are:

  * `:Dense`: A dense linear solver
  * `:Band`: A solver specialized for banded Jacobians. If used, you must set the position of the upper and lower non-zero diagonals via `jac_upper` and `jac_lower`.
  * `:LapackDense`: A version of the dense linear solver that uses the Julia-provided OpenBLAS-linked LAPACK for multithreaded operations. This will be faster than `:Dense` on larger systems but has noticeable overhead on smaller (<100 ODE) systems.
  * `:LapackBand`: A version of the banded linear solver that uses the Julia-provided OpenBLAS-linked LAPACK for multithreaded operations. This will be faster than `:Band` on larger systems but has noticeable overhead on smaller (<100 ODE) systems.
  * `:GMRES`: A GMRES method. Recommended first choice Krylov method.
  * `:BCG`: A biconjugate gradient method
  * `:PCG`: A preconditioned conjugate gradient method. Only for symmetric linear systems.
  * `:TFQMR`: A TFQMR method.
  * `:KLU`: A sparse factorization method. Requires that the user specify a Jacobian. The Jacobian must be set as a sparse matrix in the `ODEProblem` type.

The choices for globalization strategy are:

  * `:None`: No globalization strategy
  * `:LineSearch`: A line search globalization strategy

Other options:

  * `maxsetupcalls`: Maximum number of nonlinear iterations that can be performed between calls to the preconditioner or Jacobian setup function.
