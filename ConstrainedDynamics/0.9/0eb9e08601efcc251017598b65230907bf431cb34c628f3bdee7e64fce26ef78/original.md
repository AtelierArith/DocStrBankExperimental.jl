```
simulate!(mechanism, tend, args..., kwargs)
```

Simulate a mechanism for `tend` seconds. The time step has been set in mechanism.

A controller or control function (see [`Controller`](@ref)) can be passed in with `args`. If no controller is needed, nothing needs to be passed in.

Available kwargs:

  * `record`:     Specify if the state trajectory should be stored (`true`) or not (`false`).
  * `ε`:          Solver tolerance.
