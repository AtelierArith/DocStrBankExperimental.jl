```
add_low_frequency_disturbance(sys::StateSpace; ϵ = 0, measurement = false)
add_low_frequency_disturbance(sys::StateSpace, Cd; ϵ = 0, measurement = false)
```

Augment `sys` with a low-frequency (integrating if `ϵ=0`) disturbance model. If an integrating input disturbance is used together with an observer, the controller will have integral action.

  * `Cd`: If adding an input disturbance. this matrix indicates how the disturbance states affect the states of `sys`, and defaults to `sys.B`. If `measurement=true`, this matrix indicates how the disturbance states affect the outputs of `sys`, and defaults to `I(sys.ny)`.

# Arguments:

  * `ϵ`: Move the integrator pole `ϵ` into the stable region.
  * `measurement`: If true, the disturbance is a measurement disturbance, otherwise it's an input diturbance.
