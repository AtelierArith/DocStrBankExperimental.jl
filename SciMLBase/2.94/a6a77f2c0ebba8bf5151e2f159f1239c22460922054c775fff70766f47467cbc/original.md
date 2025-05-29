```julia
DiscreteCallback(condition, affect!;
    initialize = INITIALIZE_DEFAULT,
    finalize = FINALIZE_DEFAULT,
    save_positions = (true, true),
    initializealg = nothing)
```

# Arguments

  * `condition`: This is a function `condition(u,t,integrator)` for declaring when the callback should be used. A callback is initiated if the condition evaluates to `true`. See the [Integrator Interface](@ref integrator) documentation for information about `integrator`.

      * `affect!`: This is the function `affect!(integrator)` where one is allowed to modify the current state of the integrator. For more information on what can be done, see the [Integrator Interface](@ref integrator) manual page.
  * `save_positions`: Boolean tuple for whether to save before and after the `affect!`. This saving will occur just before and after the event, only at event times, and does not depend on options like `saveat`, `save_everystep`, etc. (i.e. if `saveat=[1.0,2.0,3.0]`, this can still add a save point at `2.1` if true). For discontinuous changes like a modification to `u` to be handled correctly (without error), one should set `save_positions=(true,true)`.
  * `initialize`: This is a function `(c,u,t,integrator)` which can be used to initialize the state of the callback `c`. It should modify the argument `c` and the return is ignored.
  * `finalize`: This is a function `(c,u,t,integrator)` which can be used to finalize the state of the callback `c`. It should can the argument `c` and the return is ignored.
  * `initializealg = nothing`: In the context of a DAE, this is the algorithm that is used to run initialization after the effect. The default of `nothing` defers to the initialization algorithm provided in the `solve`.

!!! warn
    The effect of using a callback with a DAE needs to be done with care because the solution `u` needs to satisfy the algebraic constraints before taking the next step. For this reason, a consistent initialization calculation must be run after running the callback. If the chosen initialization alg is `BrownBasicInit()` (the default for `solve`), then the initialization will change the algebraic variables to satisfy the conditions. Thus if `x` is an algebraic variable and the callback performs `x+=1`, the initialization may "revert" the change to satisfy the constraints. This behavior can be removed by setting `initializealg = CheckInit()`, which simply checks that the state `u` is consistent, but requires that the result of the `affect!` satisfies the constraints (or else errors). It is not recommended that `NoInit()` is used as that will lead to an unstable step following initialization. This warning can be ignored for non-DAE ODEs.

