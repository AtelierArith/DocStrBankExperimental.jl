```
ProgressMonitor(; kwargs...)
```

Print information about an ongoing simulation to the standard output at regular intervals of wall time.

# Keywords

  * `frequency = 10`: The wall-time interval (in seconds) between each progress report. Reports are always displayed at the end of a time step, if the wall time since the previous report exceeds the specified interval.
  * `always_update = true`: Print a dot after each time step between regular reports to indicate the ongoing progress of the simulation.
  * `tstep = nothing`: Passing the time step $Δt$ to the `ProgressMonitor` allows computing an advective Courant number $C = Δt / (∂₃^{max} |u|^{max})$. If not set, the advective time scale $1 / (∂₃^{max} |u|^{max})$ is reported instead.
