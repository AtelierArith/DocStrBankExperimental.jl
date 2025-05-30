```
move_detect(::Holtz, x::AbstractVector; kwargs...)
```

Implements movement detection from Identifying Movement Onset Times for a Bed-Based  Pressure Sensor Array - 2006, Holtzman.

# Arguments:

  * `L` : Length of window for moving moving_stats.
  * `κ` : Magnitude of the control signal.
  * `min_samples` : The minimum number of samples that a movement is allowed to be.
