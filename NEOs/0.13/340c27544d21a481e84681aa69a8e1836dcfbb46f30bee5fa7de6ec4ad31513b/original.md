```
propagate(dynamics::D, jd0::V, tspan::T, q0::Vector{U},
    params::NEOParameters{T}) where {T <: Real, U <: Number, V <: Number, D}
```

Integrate an orbit via the Taylor method. The initial Julian date `jd0` is assumed to be in TDB time scale.

## Arguments

  * `dynamics::D`: dynamical model function.
  * `jd0::V`: initial Julian date (TDB).
  * `tspan::T`: time span of the integration [in years].
  * `q0::Vector{U}`: vector of initial conditions.
  * `params::NEOParameters{T}`: see [`NEOParameters`](@ref).
