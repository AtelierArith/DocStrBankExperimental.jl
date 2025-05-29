```
shockdecomp(model, plan, exog_data; control, solver, [options])
```

Compute the shock decomposition for the given model, plan, exogenous (shocks) data and control solution.

If the `control` option is not specified we use the steady state solution stored in the model instance. The algorithm assumes that `control` is a solution to the dynamic model for the given plan range and final condition. We verify the residual and issue a warning, but do not enforce this. See [`steadystatedata`](@ref).

As part of the algorithm we run a simulation with the given plan, data and solver.  See [`simulate`](@ref) for additional options that control the simulation.

Note that unlike [`simulate`](@ref), here we require `exogdata` and `control` to be `MVTSeries`, i.e. plain `Array` or `Workspace` are not allowed. 

The returned value is a `Workspace` with three things in it: `c` contains a copy of `control`, `s` contains the simulated solution for the given `plan` and `exogdata` and `sd` contains the shock decomposition data. The data in `sd` is organized as a `Workspace` containing an `MVTSeries` for each variable,
