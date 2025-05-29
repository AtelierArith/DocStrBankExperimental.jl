```
sgp4(Δt::Number, tle::TLE; kwargs...)
sgp4(epoch::Tepoch, n₀::Number, e₀::Number, i₀::Number, Ω₀::Number, ω₀::Number, M₀::Number, bstar::Number; kwargs...) where {Tepoch<:Number, T<:Number}
```

Initialize the SGP4 structure and propagate the orbit until the time Δt [min].

# Arguments

  * `epoch::Number`: Epoch of the orbital elements [Julian Day].
  * `n₀::Number`: SGP type "mean" mean motion at epoch [rad/min].
  * `e₀::Number`: "Mean" eccentricity at epoch.
  * `i₀::Number`: "Mean" inclination at epoch [rad].
  * `Ω₀::Number`: "Mean" longitude of the ascending node at epoch [rad].
  * `ω₀::Number`: "Mean" argument of perigee at epoch [rad].
  * `M₀::Number`: "Mean" mean anomaly at epoch [rad].
  * `bstar::Number`: Drag parameter (B*).
  * `tle::TLE`: TLE to initialize the SPG4 (see `TLE`).

# Keywords

  * `spg4_gc::Sgp4Constants`: SPG4 orbit propagator constants (see [`Sgp4Constants`](@ref)).   (**Default** = `sgp4c_wgs84`)

# Returns

  * `SVector{3, T}`: The position vector [km].
  * `SVector{3, T}`: The velocity vector [km/s].
  * [`Sgp4Propagator`](@ref): The SGP4 orbit propagator structure.
