```
add_disturbance(sys::StateSpace, Ad::Matrix, Cd::Matrix)
```

See CCS pp. 144

# Arguments:

  * `sys`: System to augment
  * `Ad`: The dynamics of the disturbance
  * `Cd`: How the disturbance states affect the states of `sys`. This matrix has the shape (sys.nx, size(Ad, 1))

See also [`add_low_frequency_disturbance`](@ref), [`add_resonant_disturbance`](@ref)
