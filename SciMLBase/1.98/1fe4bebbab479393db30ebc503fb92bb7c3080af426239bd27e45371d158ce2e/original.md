```julia
ContinuousCallback(condition,affect!,affect_neg!;
                   initialize = INITIALIZE_DEFAULT,
                   finalize = FINALIZE_DEFAULT,
                   idxs = nothing,
                   rootfind=LeftRootFind,
                   save_positions=(true,true),
                   interp_points=10,
                   abstol=10eps(),reltol=0,repeat_nudge=1//100)
```

```julia
function ContinuousCallback(condition,affect!;
                   initialize = INITIALIZE_DEFAULT,
                   finalize = FINALIZE_DEFAULT,
                   idxs = nothing,
                   rootfind=LeftRootFind,
                   save_positions=(true,true),
                   affect_neg! = affect!,
                   interp_points=10,
                   abstol=10eps(),reltol=0,repeat_nudge=1//100)
```

Contains a single callback whose `condition` is a continuous function. The callback is triggered when this function evaluates to 0.

# Arguments

  * `condition`: This is a function `condition(u,t,integrator)` for declaring when the callback should be used. A callback is initiated if the condition hits `0` within the time interval. See the [Integrator Interface](@ref integrator) documentation for information about `integrator`.
  * `affect!`: This is the function `affect!(integrator)` where one is allowed to modify the current state of the integrator. If you do not pass an `affect_neg!` function, it is called when `condition` is found to be `0` (at a root) and the cross is either an upcrossing (from negative to positive) or a downcrossing (from positive to negative). You need to explicitly pass `nothing` as the `affect_neg!` argument if it should only be called at upcrossings, e.g. `ContinuousCallback(condition, affect!, nothing)`. For more information on what can be done, see the [Integrator Interface](@ref integrator) manual page. Modifications to `u` are safe in this function.
  * `affect_neg!=affect!`: This is the function `affect_neg!(integrator)` where one is allowed to modify the current state of the integrator. This is called when `condition` is found to be `0` (at a root) and the cross is a downcrossing (from positive to negative). For more information on what can be done, see the [Integrator Interface](@ref integrator) manual page. Modifications to `u` are safe in this function.
  * `rootfind=LeftRootFind`: This is a flag to specify the type of rootfinding to do for finding event location. If this is set to `LeftRootfind`, the solution will be backtracked to the point where `condition==0` and if the solution isn't exact, the left limit of root is used. If set to `RightRootFind`, the solution would be set to the right limit of the root. Otherwise, the systems and the `affect!` will occur at `t+dt`. Note that these enums are not exported, and thus one needs to reference them as `SciMLBase.LeftRootFind`, `SciMLBase.RightRootFind`, or `SciMLBase.NoRootFind`.
  * `interp_points=10`: The number of interpolated points to check the condition. The condition is found by checking whether any interpolation point / endpoint has a different sign. If `interp_points=0`, then conditions will only be noticed if the sign of `condition` is different at `t` than at `t+dt`. This behavior is not robust when the solution is oscillatory, and thus it's recommended that one use some interpolation points (they're cheap to compute!). `0` within the time interval.
  * `save_positions=(true,true)`: Boolean tuple for whether to save before and after the `affect!`. This saving will occur just before and after the event, only at event times, and does not depend on options like `saveat`, `save_everystep`, etc. (i.e. if `saveat=[1.0,2.0,3.0]`, this can still add a save point at `2.1` if true). For discontinuous changes like a modification to `u` to be handled correctly (without error), one should set `save_positions=(true,true)`.
  * `idxs=nothing`: The components which will be interpolated into the condition. Defaults to `nothing` which means `u` will be all components.
  * `initialize`: This is a function `(c,u,t,integrator)` which can be used to initialize the state of the callback `c`. It should modify the argument `c` and the return is ignored.
  * `finalize`: This is a function `(c,u,t,integrator)` which can be used to finalize the state of the callback `c`. It can modify the argument `c` and the return is ignored.
  * `abstol=1e-14` & `reltol=0`: These are used to specify a tolerance from zero for the rootfinder: if the starting condition is less than the tolerance from zero, then no root will be detected. This is to stop repeat events happening immediately after a rootfinding event.
  * `repeat_nudge = 1//100`: This is used to set the next testing point after a previously found zero. Defaults to 1//100, which means after a callback, the next sign check will take place at t + dt*1//100 instead of at t to avoid repeats.
