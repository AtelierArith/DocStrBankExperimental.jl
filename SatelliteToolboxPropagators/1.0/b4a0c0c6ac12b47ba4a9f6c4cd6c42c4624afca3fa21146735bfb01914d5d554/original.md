```
twobody!(tbd::TwoBodyPropagator{Tepoch, T}, t::Number) where {Tepoch, T} -> SVector{3, T}, SVector{3, T}
```

Propagate the orbit defined in `tbd` (see [`TwoBodyPropagator`](@ref)) to `t` [s] after the epoch of the input mean elements in `tbd`.

!!! note
    The internal values in `tbd` will be modified.


# Returns

  * `SVector{3, T}`: Position vector [m] represented in the inertial frame at propagation   instant.
  * `SVector{3, T}`: Velocity vector [m / s] represented in the inertial frame at propagation   instant.

# Remarks

The inertial frame in which the output is represented depends on which frame it was used to generate the orbit parameters.
