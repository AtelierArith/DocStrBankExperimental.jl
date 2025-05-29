```
obsposECEF(observatory::ObservatoryMPC{T}; kwarg) where {T <: AbstractFloat}
obsposECEF(x::RadecMPC{T}; kwarg) where {T <: AbstractFloat}
obsposECEF(x::RadarJPL{T}; kwarg) where {T <: AbstractFloat}
```

Return the observer's geocentric `[x, y, z]` position vector in Earth-Centered Earth-Fixed (ECEF) reference frame.

# Keyword argument

  * `eop::Union{EopIau1980, EopIau2000A}`: Earth Orientation Parameters (eop).
