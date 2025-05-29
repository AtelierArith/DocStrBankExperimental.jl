```
explicit_unsteady(initialize, onestep, solve, t, xd, xc, p=(); cache=nothing)
```

Make reverse-mode efficient for explicit ODEs Builds tape over each time step separately and analytically propagates between, rather than recording a long tape over the entire time sequence.

# Arguments:

  * `initialize::function`: Return initial state variables.  `y0 = initialize(t0, xd, xc0, p)`. May or may not depend   on t0 (initial time), xd (design variables), xc0 (initial control variables), p (fixed parameters)
  * `onestep::function`: define how states are updated (assuming one-step methods). `y = onestep(yprev, t, tprev, xd, xci, p)`   or in-place `onestep!(y, yprev, t, tprev, xd, xci, p)`.  Set the next set of state variables `y`, given the previous state `yprev`,   current time `t`, previous time `tprev`, design variables `xd`, current control variables `xc`, and fixed parameters `p`.
  * `t::vector{float}`: time steps that simulation runs across
  * `xd::vector{float}`: design variables, don't change in time, but do change from one run to the next (otherwise they would be parameters)
  * `xc::matrix{float}`, size nxc x nt: control variables. xc[:, i] are the control variables at the ith time step.
  * `p::tuple`: fixed parameters, i.e., they are always constant and so do not affect derivatives.  Default is empty tuple.

# Keyword Arguments:

  * `cache=nothing`: see `explicit_unsteady_cache`.  If computing derivatives more than once, you should compute the  cache beforehand the save for later iterations.  Otherwise, it will be created internally.
