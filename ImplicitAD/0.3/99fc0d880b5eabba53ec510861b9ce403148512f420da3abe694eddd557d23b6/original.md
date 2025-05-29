```
implicit_unsteady(initialize, onestep, residual, t, xd, xc, p=(); cache=nothing, drdy=drdy_forward, lsolve=linear_solve)
```

Make reverse-mode efficient for implicit ODEs (solvers compatible with AD).

# Arguments:

  * `initialize::function`: Return initial state variables.  `y0 = initialize(t0, xd, xc0, p)`. May or may not depend   on t0 (initial time), xd (design variables), xc0 (initial control variables), p (fixed parameters)
  * `onestep::function`: define how states are updated (assuming one-step methods) including any solver. `y = onestep(yprev, t, tprev, xd, xci, p)`   or in-place `onestep!(y, yprev, t, tprev, xd, xci, p)`.  Set the next set of state variables `y`, given the previous state `yprev`,   current time `t`, previous time `tprev`, design variables `xd`, current control variables for that time step `xci`, and fixed parameters `p`.
  * `residual::function`: define residual that is solved in onestep.  Either `r = residual(y, yprev, t, tprev, xd, xci, p)` where variables are same as above or   `residual!(r, y, yprev, t, tprev, xd, xci, p)`.
  * `t::vector{float}`: time steps that simulation runs across
  * `xd::vector{float}`: design variables, don't change in time, but do change from one run to the next (otherwise they would be parameters)
  * `xc::matrix{float}`, size nxc x nt: control variables. xc[:, i] are the control variables at the ith time step.
  * `p::tuple`: fixed parameters, i.e., they are always constant and so do not affect derivatives.  Default is empty tuple.

# Keyword Arguments:

  * `cache=nothing`: see `implicit_unsteady_cache`.  If computing derivatives more than once, you should compute the   cache beforehand the save for later iterations.  Otherwise, it will be created internally.
  * `drdy`: drdy(residual, r, y, yprev, t, tprev, xd, xci, p). Provide (or compute yourself): ∂ri/∂yj.  Default is   forward mode AD.
  * `lsolve::function`: `lsolve(A, b)`. Linear solve `A x = b` (where `A` is computed in  `drdy` and `b` is computed in `jvp`, or it solves `A^T x = c` where `c` is computed  in `vjp`). Default is backslash operator.
