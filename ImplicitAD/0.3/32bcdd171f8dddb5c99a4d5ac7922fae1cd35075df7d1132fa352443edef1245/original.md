```
explicit_unsteady_cache(initialize, onestep!, ny, nxd, nxc, p=(); compile=false)
```

Initialize arrays and functions needed for explicit_unsteady reverse mode

# Arguments

  * `initialize::function`: Return initial state variables.  `y0 = initialize(t0, xd, xc0, p)`. May or may not depend   on t0 (initial time), xd (design variables), xc0 (initial control variables), p (fixed parameters)
  * `onestep::function`: define how states are updated (assuming one-step methods). `y = onestep(yprev, t, tprev, xd, xci, p)`   or in-place `onestep!(y, yprev, t, tprev, xd, xci, p)`.  Set the next set of state variables `y`, given the previous state `yprev`,   current time `t`, previous time `tprev`, design variables `xd`, current control variables for that time step `xci`, and fixed parameters `p`.
  * `ny::int`: number of states
  * `nxd::int`: number of design variables
  * `nxc::int`: number of control variables (at a given time step)
  * `p::tuple`: fixed parameters, i.e., they are always constant and so do not affect derivatives.  Default is empty tuple.
  * `compile::bool`: indicates whether the tape for the function `onestep` can be  prerecorded.  Will be much faster but should only be `true` if `onestep` does not contain any branches.  Otherwise, ReverseDiff may return incorrect gradients.
