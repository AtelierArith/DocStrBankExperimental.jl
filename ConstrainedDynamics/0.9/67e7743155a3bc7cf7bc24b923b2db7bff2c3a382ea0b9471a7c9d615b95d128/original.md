```
simulate!(mechanism, storage, args..., kwargs)
```

Simulate a mechanism for the number of time steps specified by `storage` (see [`Storage`](@ref)). The time step has been set in mechanism. 

This method can be used to debug potentially faulty (instable) controllers: Even if the simulation fails, the results up to the point of failure are stored in `storage` and can be analyzed and visualized.

A controller or control function (see [`Controller`](@ref)) can be passed in with `args`. If no controller is needed, nothing needs to be passed in.

Available kwargs:

  * `record`:     Specify if the state trajectory should be stored (`true`) or not (`false`).
  * `ε`:          Solver tolerance.
