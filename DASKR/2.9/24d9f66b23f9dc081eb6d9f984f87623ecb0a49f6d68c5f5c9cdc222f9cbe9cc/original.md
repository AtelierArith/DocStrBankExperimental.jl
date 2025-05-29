```julia
function daskr(;linear_solver=:Dense,
                  jac_upper=0,jac_lower=0,max_order = 5,
                  non_negativity_enforcement = 0,
                  non_negativity_enforcement_array = nothing,
                  max_krylov_iters = nothing,
                  num_krylov_vectors = nothing,
                  max_number_krylov_restarts = 5,
                  krylov_convergence_test_constant = 0.05,
                  exclude_algebraic_errors = false)
```

This is a wrapper for the well-known DASKR algorithm.

DASKR is a solver for systems of differential-algebraic equations (DAEs). It includes options for both direct and iterative (Krylov) methods for the solution of the linear systems arising at each (implicit) time step. DASKR is a variant of the DASPK package [1].  In addition to all the capabilities of DASPK, DASKR includes the ability to find the roots of a given set of functions while integrating the DAE system.

In contrast to the older DASSL package, DASKR includes a procedure for calculating consistent initial conditions for a large class of problems (which includes semi-explicit index-1 systems) [2].  This procedure includes options for inequality constraints on selected components.  The package also includes an option to omit the algebraic components from the local error control.

### Linear Solver Choice

Choices for the linear solver are:

  * `:Dense`
  * `:Banded`
  * `:SPIGMR`, a Krylov method

### Other Keyword Arguments

  * `jac_upper=0,jac_lower=0`: used for setting the upper and lower bands for a banded Jacobian. Defaults to 0. Ignored unless the linear solver is `:Banded`.
  * `max_order = 5`: the maximum order of the BDF method.
  * `non_negativity_enforcement = 0`, whether to enforce non-negativty in the solution. Defaults to `0` or false, can be set to `1` to enable.
  * `non_negativity_enforcement_array = nothing`, an array of 0's and 1's for specifying non-negativity enforcement to a subset of states.
  * `max_krylov_iters=nothing`: maximum number of iterations for the Krylov subspace linear solver before rejecting a step. Defaults to `nothing` or an automatic detection.
  * `num_krylov_vectors=nothing`: maximum number of history states in the GMRES vector. Defaults to `nothing` or an automatic choice
  * `max_number_krylov_restarts=5`: If you figure out what this is, open an issue or PR.
  * `krylov_convergence_test_constant = 0.05`: Some constant in DASKR's convergence test.
  * `exclude_algebraic_errors = false`: whether algebraic variables are included in the adaptive time stepping error check. Defaults to false.
