```
COLNEW(; bvpclass = 1, collocationpts = 7, diagnostic_output = 1,
    max_num_subintervals = 3000, bc_func = nothing, dbc_func = nothing,
    zeta = nothing)
COLNEW(bvpclass::Int, collocationpts::Int, diagnostic_output::Int,
    max_num_subintervals::Int, bc_func, dbc_func, zeta::AbstractVector)
```

## Keyword Arguments:

  * `bvpclass`: Boundary value problem classification, default as nonlinear and "extra sensitive", available choices:

      * `0`: Linear boundary value problem.
      * `1`: Nonlinear and regular.
      * `2`: Nonlinear and "extra sensitive" (first relax factor is rstart and the nonlinear iteration does not rely on past convergence).
      * `3`: fail-early: return immediately upon: a) two successive non-convergences. b) after obtaining an error estimate for the first time.
  * `collocationpts`: Number of collocation points per subinterval. Require orders[i] ≤ k ≤ 7, default as 7
  * `diagnostic_output`: Diagnostic output for COLNEW, default as no printout, available choices:

      * `-1`: Full diagnostic printout.
      * `0`: Selected printout.
      * `1`: No printout.
  * `max_num_subintervals`: Number of maximal subintervals, default as 3000.
  * `bc_func`: Boundary condition accord with ODEInterface.jl, only used for multi-points BVP.
  * `dbc_func`: Jacobian of boundary condition accord with ODEInterface.jl, only used for multi-points BVP.
  * `zeta`: The points in interval where boundary conditions are specified, only used for multi-points BVP.

A Fortran77 code solves a multi-points boundary value problems for a mixed order system of ODEs. It incorporates a new basis representation replacing b-splines, and improvements for the linear and nonlinear algebraic equation solvers.

!!! warning
    Only supports two-point boundary value problems.


!!! note
    Only available if the `ODEInterface` package is loaded.

