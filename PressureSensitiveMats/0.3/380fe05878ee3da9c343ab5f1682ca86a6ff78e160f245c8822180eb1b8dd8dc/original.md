```
move_detect(::Solei, x::AbstractVector; kwargs...)
```

Implements movement detection from Movement Detection with Adaptive Window Length for  Unobtrusive Bed-based Pressure-Sensor Array - 2017, Soleimani

# Arguments:

  * `L` : Length of window for moving moving_stats.
  * `α=-0.029` : Threshold of first differences for the offset
  * `κ=3` : Magnitude of the control signal.
  * `min_samples=2` : The minimum number of samples that a movement is allowed to be.
  * `height=50` : Subject height in cm. Default to cancel out weight in ρ calculation.
  * `weight=50` : Subject weight in kg. Default to cancel out height in ρ calculation.
