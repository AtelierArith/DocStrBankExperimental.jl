```julia
simulate!(model, ti, dt, tf; kwargs...)

```

Simulates the `model` starting from the initial time `t0` until the final time `tf` with the sampling interval of `tf`. For `kwargs` are 

  * `logtofile::Bool`: If `true`, a log file is contructed logging each step of the simulation.
  * `reportsim::Bool`: If `true`, `model` components are written files after the simulation. When this file is read back, the model components can be consructed back with their status at the end of the simulation.
  * `simdir::String`: The path of the directory in which simulation file are recorded.
