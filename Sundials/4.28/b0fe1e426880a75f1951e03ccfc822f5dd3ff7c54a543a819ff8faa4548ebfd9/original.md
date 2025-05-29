```julia
ARKODE(stiffness=Sundials.Implicit();
      method=:Newton,linear_solver=:Dense,
      jac_upper=0,jac_lower=0,stored_upper = jac_upper+jac_lower,
      non_zero=0,krylov_dim=0,
      max_hnil_warns = 10,
      max_error_test_failures = 7,
      max_nonlinear_iters = 3,
      max_convergence_failures = 10,
      predictor_method = 0,
      nonlinear_convergence_coefficient = 0.1,
      dense_order = 3,
      order = 4,
      set_optimal_params = false,
      crdown = 0.3,
      dgmax = 0.2,
      rdiv = 2.3,
      msbp = 20,
      adaptivity_method = 0,
      prec = nothing, psetup = nothing, prec_side = 0
      )
```

ARKODE: Explicit and ESDIRK Runge-Kutta methods of orders 2-8 depending on choice of options.

### Tableau Choices

The main options for ARKODE are the choice between explicit and implicit and the method order, given via:

ARKODE(Sundials.Explicit()) # Solve with explicit tableau of default order 4 ARKODE(Sundials.Implicit(),order = 3) # Solve with explicit tableau of order 3

The order choices for explicit are 2 through 8 and for implicit 3 through 5. Specific methods can also be set through the etable and itable options for explicit and implicit tableaus respectively. The available tableaus are:

etable:

  * HEUN*EULER*2*1*2: 2nd order Heun's method
  * BOGACKI*SHAMPINE*4*2*3:
  * ARK324L2SA*ERK*4*2*3: explicit portion of Kennedy and Carpenter's 3rd order method
  * ZONNEVELD*5*3_4: 4th order explicit method
  * ARK436L2SA*ERK*6*3*4: explicit portion of Kennedy and Carpenter's 4th order method
  * SAYFY*ABURUB*6*3*4: 4th order explicit method
  * CASH*KARP*6*4*5: 5th order explicit method
  * FEHLBERG*6*4_5: Fehlberg's classic 5th order method
  * DORMAND*PRINCE*7*4*5: the classic 5th order Dormand-Prince method
  * ARK548L2SA*ERK*8*4*5: explicit portion of Kennedy and Carpenter's 5th order method
  * VERNER*8*5_6: Verner's classic 5th order method
  * FEHLBERG*13*7_8: Fehlberg's 8th order method

itable:

  * SDIRK*2*1_2: An A-B-stable 2nd order SDIRK method
  * BILLINGTON*3*3_2: A second order method with a 3rd order error predictor of less stability
  * TRBDF2*3*3_2: The classic TR-BDF2 method
  * KVAERNO*4*2_3: an L-stable 3rd order ESDIRK method
  * ARK324L2SA*DIRK*4*2*3: implicit portion of Kennedy and Carpenter's 3th order method
  * CASH*5*2_4: Cash's 4th order L-stable SDIRK method
  * CASH*5*3_4: Cash's 2nd 4th order L-stable SDIRK method
  * SDIRK*5*3_4: Hairer's 4th order SDIRK method
  * KVAERNO*5*3_4: Kvaerno's 4th order ESDIRK method
  * ARK436L2SA*DIRK*6*3*4: implicit portion of Kennedy and Carpenter's 4th order method
  * KVAERNO*7*4_5: Kvaerno's 5th order ESDIRK method
  * ARK548L2SA*DIRK*8*4*5: implicit portion of Kennedy and Carpenter's 5th order method

These can be set for example via:

```julia
ARKODE(Sundials.Explicit(),etable = Sundials.DORMAND_PRINCE_7_4_5)
ARKODE(Sundials.Implicit(),itable = Sundials.KVAERNO_4_2_3)
```

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

See the [ARKODE manual](https://computing.llnl.gov/sites/default/files/ark_guide-4.7.0.pdf) for details on the additional options.
