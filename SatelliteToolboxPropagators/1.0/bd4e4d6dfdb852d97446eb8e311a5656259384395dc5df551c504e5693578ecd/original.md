```
j4!(j4d::J4Propagator{Tepoch, T}, t::Number) where {Tepoch<:Number, T<:Number} -> SVector{3, T}, SVector{3, T}
```

Propagate the orbit defined in `j4d` (see [`J4Propagator`](@ref)) to `t` [s] after the epoch of the input mean elements in `j4d`.

!!! note
    The internal values in `j4d` will be modified.


# Returns

  * `SVector{3, T}`: Position vector [m] represented in the inertial frame at propagation   instant.
  * `SVector{3, T}`: Velocity vector [m / s] represented in the inertial frame at propagation   instant.

# Remarks

The inertial frame in which the output is represented depends on which frame it was used to generate the orbit parameters. Notice that the perturbation theory requires an inertial frame with true equator.
