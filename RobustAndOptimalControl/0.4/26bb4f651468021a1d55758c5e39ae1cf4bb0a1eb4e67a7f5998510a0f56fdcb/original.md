```
add_resonant_disturbance(sys::StateSpace{Continuous}, ω, ζ, Ai::Int; measurement = false)
```

Augment `sys` with a resonant disturbance model.

# Arguments:

  * `ω`: Frequency
  * `ζ`: Relative damping.
  * `Ai`: The affected state
  * `measurement`: If true, the disturbace is acting on the output, this will cause the controller to have zeros at ω (roots of poly s² + 2ζωs + ω²). If false, the disturbance is acting on the input, this will cause the controller to have poles at ω (roots of poly s² + 2ζωs + ω²).
