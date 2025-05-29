```
run!(sim::SimulationWorkspace, dt::Float64, t_end::Float64, step!::Function; kwargs...)
```

A utility function for time-marching and exporting the results.  Specify the time step `dt`, final time `t_end` and a function  $step!(sim::SimulationWorkspace, time::Float64).$ Keyword arguments:

  * `nframes::Bool` (how many times should I export the data?)
  * `path::String` (where to export the data?)
  * `save_points::Bool` (should I export the point data?)
  * `save_grid:::Bool` (should I export the grid data?)
  * `save_csv::Bool` (should I export global variables as a csv data?)
  * `vtp_vars` (which local variables should I export?)
  * `csv_vars` (which global variables should I export?)
  * `postproc!::Function` (If provided, `postproc!(sim, dt)` is called each time just before the data is saved.

Use this for some (expensive) post proccessing that affects the output files, not the simulation itself.)

Note this assumes constant time step. See `examples/sedov.jl` for an example with adaptive time step.
