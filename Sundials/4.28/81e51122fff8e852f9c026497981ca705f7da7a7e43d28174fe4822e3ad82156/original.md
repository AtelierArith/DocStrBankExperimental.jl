```julia
CVODE_BDF(;method=:Newton,linear_solver=:Dense,
          jac_upper=0,jac_lower=0,
          stored_upper = jac_upper + jac_lower,
          non_zero=0,krylov_dim=0,
          stability_limit_detect=false,
          max_hnil_warns = 10,
          max_order = 5,
          max_error_test_failures = 7,
          max_nonlinear_iters = 3,
          max_convergence_failures = 10,
          prec = nothing, prec_side = 0)
```

CVODE_BDF: CVode Backward Differentiation Formula (BDF) solver.

### Method Choices

  * method - This is the method for solving the implicit equation. For BDF this defaults to   :Newton while for Adams this defaults to :Functional. These choices match the   recommended pairing in the Sundials.jl manual. However, note that using the :Newton   method may take less iterations but requires more memory than the :Function iteration   approach.
  * linear_solver - This is the linear solver which is used in the :Newton method.

### Linear Solver Choices

The choices for the linear solver are:

  * :Dense - A dense linear solver.
  * :Band - A solver specialized for banded Jacobians. If used, you must set the position of the upper and lower non-zero diagonals via jac*upper and jac*lower.
  * :LapackDense - A version of the dense linear solver that uses the Julia-provided OpenBLAS-linked LAPACK for multithreaded operations. This will be faster than :Dense on larger systems but has noticable overhead on smaller (<100 ODE) systems.
  * :LapackBand - A version of the banded linear solver that uses the Julia-provided OpenBLAS-linked LAPACK for multithreaded operations. This will be faster than :Band on larger systems but has noticable overhead on smaller (<100 ODE) systems.
  * :Diagonal - This method is specialized for diagonal Jacobians.
  * :GMRES - A GMRES method. Recommended first choice Krylov method
  * :BCG - A Biconjugate gradient method.
  * :PCG - A preconditioned conjugate gradient method. Only for symmetric linear systems.
  * :TFQMR - A TFQMR method.
  * :KLU - A sparse factorization method. Requires that the user specifies a Jacobian. The Jacobian must be set as a sparse matrix in the ODEProblem type.

Example:

```julia
CVODE_BDF() # BDF method using Newton + Dense solver
CVODE_BDF(method=:Functional) # BDF method using Functional iterations
CVODE_BDF(linear_solver=:Band,jac_upper=3,jac_lower=3) # Banded solver with nonzero diagonals 3 up and 3 down
CVODE_BDF(linear_solver=:BCG) # Biconjugate gradient method
```

### Preconditioners

Note that here `prec` is a preconditioner function `prec(z,r,p,t,y,fy,gamma,delta,lr)` where:

  * `z`: the computed output vector
  * `r`: the right-hand side vector of the linear system
  * `p`: the parameters
  * `t`: the current independent variable
  * `du`: the current value of `f(u,p,t)`
  * `gamma`: the `gamma` of `W = M - gamma*J`
  * `delta`: the iterative method tolerance
  * `lr`: a flag for whether `lr=1` (left) or `lr=2` (right) preconditioning

and `psetup` is the preconditioner setup function for pre-computing Jacobian information `psetup(p, t, u, du, jok, jcurPtr, gamma)`. Where:

  * `p`: the parameters
  * `t`: the current independent variable
  * `u`: the current state
  * `du`: the current `f(u,p,t)`
  * `jok`: a bool indicating whether the Jacobian needs to be updated
  * `jcurPtr`: a reference to an Int for whether the Jacobian was updated. `jcurPtr[]=true` should be set if the Jacobian was updated, and `jcurPtr[]=false` should be set if the Jacobian was not updated.
  * `gamma`: the `gamma` of `W = M - gamma*J`

`psetup` is optional when `prec` is set.

### Additional Options

See [the CVODE manual](https://computing.llnl.gov/sites/default/files/cv_guide-5.7.0.pdf) for details on the additional options.
