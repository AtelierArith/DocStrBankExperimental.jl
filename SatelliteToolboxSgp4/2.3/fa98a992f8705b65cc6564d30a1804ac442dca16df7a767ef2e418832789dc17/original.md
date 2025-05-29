```
sgp4!(sgp4d::Sgp4Propagator{Tepoch, T}, t::Number) where T
```

Propagate the orbit defined in `sgp4d` (see [`Sgp4Propagator`](@ref)) until the time `t` [min].

!!! note
    The internal values in `sgp4d` will be modified.


# Returns

  * `SVector{T, 3}`: The position vector represented in TEME frame at time `t` [km].
  * `SVector{T, 3}`: The velocity vector represented in TEME frame at time `t` [km/s].
