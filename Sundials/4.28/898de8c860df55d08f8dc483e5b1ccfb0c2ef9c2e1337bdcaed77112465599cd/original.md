```julia
IDA(;linear_solver=:Dense,jac_upper=0,jac_lower=0,krylov_dim=0,
    max_order = 5,
    max_error_test_failures = 7,
    max_nonlinear_iters = 3,
    nonlinear_convergence_coefficient = 0.33,
    nonlinear_convergence_coefficient_ic = 0.0033,
    max_num_steps_ic = 5,
    max_num_jacs_ic = 4,
    max_num_iters_ic = 10,
    max_num_backs_ic = 100,
    use_linesearch_ic = true,
    max_convergence_failures = 10,
    init_all = false,
    prec = nothing, psetup = nothing)
```

IDA: This is the IDA method from the Sundials.jl package.

### Linear Solvers

Note that the constructors for the Sundials algorithms take a main argument: linearsolver - This is the linear solver which is used in the Newton iterations. The choices are:

  * :Dense - A dense linear solver.
  * :Band - A solver specialized for banded Jacobians. If used, you must set the position of the upper and lower non-zero diagonals via jac*upper and jac*lower.
  * :LapackDense - A version of the dense linear solver that uses the Julia-provided OpenBLAS-linked LAPACK for multithreaded operations. This will be faster than :Dense on larger systems but has noticable overhead on smaller (<100 ODE) systems.
  * :LapackBand - A version of the banded linear solver that uses the Julia-provided OpenBLAS-linked LAPACK for multithreaded operations. This will be faster than :Band on larger systems but has noticable overhead on smaller (<100 ODE) systems.
  * :GMRES - A GMRES method. Recommended first choice Krylov method
  * :BCG - A Biconjugate gradient method.
  * :PCG - A preconditioned conjugate gradient method. Only for symmetric linear systems.
  * :TFQMR - A TFQMR method.
  * :KLU - A sparse factorization method. Requires that the user specifies a Jacobian. The Jacobian must be set as a sparse matrix in the ODEProblem type.

Note that the preconditioner for iterative linear solvers (if supplied) should be a left preconditioner.

Example:

```julia
IDA() # Newton + Dense solver
IDA(linear_solver=:Band,jac_upper=3,jac_lower=3) # Banded solver with nonzero diagonals 3 up and 3 down
IDA(linear_solver=:BCG) # Biconjugate gradient method
```

### Preconditioners

Note that here `prec` is a (left) preconditioner function `prec(z,r,p,t,y,fy,gamma,delta)` where:

  * `z`: the computed output vector
  * `r`: the right-hand side vector of the linear system
  * `p`: the parameters
  * `t`: the current independent variable
  * `du`: the current value of `f(u,p,t)`
  * `gamma`: the `gamma` of `W = M - gamma*J`
  * `delta`: the iterative method tolerance

and `psetup` is the preconditioner setup function for pre-computing Jacobian information. Where:

  * `p`: the parameters
  * `t`: the current independent variable
  * `resid`: the current residual
  * `u`: the current state
  * `du`: the current derivative of the state
  * `gamma`: the `gamma` of `W = M - gamma*J`

`psetup` is optional when `prec` is set.

### Additional Options

See [the Sundials manual](https://computing.llnl.gov/sites/default/files/ida_guide-5.7.0.pdf) for details on the additional options. The option `init_all` controls the initial condition consistency routine. If the initial conditions are inconsistent (i.e. they do not satisfy the implicit equation), `init_all=false` means that the algebraic variables and derivatives will be modified in order to satisfy the DAE. If `init_all=true`, all initial conditions will be modified to satisfy the DAE.
