```
Simulation(model; Δt,
           verbose = true,
           stop_iteration = Inf,
           stop_time = Inf,
           wall_time_limit = Inf,
           minimum_relative_step = 0)
```

Construct a `Simulation` for a `model` with time step `Δt`.

# Keyword arguments

  * `Δt`: Required keyword argument specifying the simulation time step. Can be a `Number`       for constant time steps or a `TimeStepWizard` for adaptive time-stepping.
  * `stop_iteration`: Stop the simulation after this many iterations.
  * `stop_time`: Stop the simulation once this much model clock time has passed.
  * `wall_time_limit`: Stop the simulation if it's been running for longer than this many                    seconds of wall clock time.
  * `minimum_relative_step`: time steps smaller than `Δt * minimum_relative_step` will be skipped.                          This avoids extremely high values when writing the pressure to disk.                          Default value is 0. See github.com/CliMA/Oceananigans.jl/issues/3593 for details.
