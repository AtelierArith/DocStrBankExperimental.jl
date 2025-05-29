```julia
DiscreteCallback(condition,affect!;
                 initialize = INITIALIZE_DEFAULT,
                 finalize = FINALIZE_DEFAULT,
                 save_positions=(true,true))
```

# Arguments

  * `condition`: This is a function `condition(u,t,integrator)` for declaring when the callback should be used. A callback is initiated if the condition evaluates to `true`. See the [Integrator Interface](@ref integrator) documentation for information about `integrator`.

      * `affect!`: This is the function `affect!(integrator)` where one is allowed to

    modify the current state of the integrator. For more information on what can be done, see the [Integrator Interface](@ref integrator) manual page.
  * `save_positions`: Boolean tuple for whether to save before and after the `affect!`. This saving will occur just before and after the event, only at event times, and does not depend on options like `saveat`, `save_everystep`, etc. (i.e. if `saveat=[1.0,2.0,3.0]`, this can still add a save point at `2.1` if true). For discontinuous changes like a modification to `u` to be handled correctly (without error), one should set `save_positions=(true,true)`.
  * `initialize`: This is a function `(c,u,t,integrator)` which can be used to initialize the state of the callback `c`. It should modify the argument `c` and the return is ignored.
  * `finalize`: This is a function `(c,u,t,integrator)` which can be used to finalize the state of the callback `c`. It should can the argument `c` and the return is ignored.
