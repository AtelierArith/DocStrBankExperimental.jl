```
implicit_unsteady_cache(initialize, residual, ny, nxd, nxc, p=(); compile=false)
```

Initialize arrays and functions needed for implicit_unsteady reverse mode

# Arguments

  * `initialize::function`: Return initial state variables.  `y0 = initialize(t0, xd, xc0, p)`. May or may not depend   on t0 (initial time), xd (design variables), xc0 (initial control variables), p (fixed parameters)
  * `residual::function`: define residual that is solved in onestep.  Either `r = residual(y, yprev, t, tprev, xd, xci, p)` where variables are same as above   `residual!(r, y, yprev, t, tprev, xd, xci, p)`.
  * `ny::int`: number of states
  * `nxd::int`: number of design variables
  * `nxc::int`: number of control variables (at a given time step)
  * `p::tuple`: fixed parameters, i.e., they are always constant and so do not affect derivatives.  Default is empty tuple.
  * `compile::bool`: indicates whether the tape for the function `onestep` can be  prerecorded.  Will be much faster but should only be `true` if `onestep` does not contain any branches.  Otherwise, ReverseDiff may return incorrect gradients.
