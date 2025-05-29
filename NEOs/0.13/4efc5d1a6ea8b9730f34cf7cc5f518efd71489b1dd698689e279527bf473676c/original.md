```
obsposvelECI(observatory::ObservatoryMPC{T}, et::U; kwarg) where {T <: AbstractFloat, U <: Number}
obsposvelECI(x::RadecMPC{T}; kwarg) where {T <: AbstractFloat}
obsposvelECI(x::RadarJPL{T}; kwarg) where {T <: AbstractFloat}
```

Return the observer's geocentric `[x, y, z, v_x, v_y, v_z]` "state" vector in Earth-Centered Inertial (ECI) reference frame. By default, the IAU200A Earth orientation model is used to transform from Earth-centered, Earth-fixed (ECEF) frame to ECI frame. Other Earth orientation models, such as the IAU1976/80 model, can be used by importing the `SatelliteToolboxTransformations.EopIau1980` type and passing it to the `eop` keyword argument in the function call.

See also [`SatelliteToolboxBase.OrbitStateVector`](@ref) and [`SatelliteToolboxTransformations.sv_ecef_to_eci`](@ref).

# Arguments

  * `observatory::ObservatoryMPC{T}`: observation site.
  * `et::U`: ephemeris time (TDB seconds since J2000.0 epoch).
  * `x::RadecMPC{T}/RadarJPL{T}`: astrometric observation.

# Keyword argument

  * `eop::Union{EopIau1980, EopIau2000A}`: Earth Orientation Parameters (eop).
