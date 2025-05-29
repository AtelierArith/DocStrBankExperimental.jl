```
propagate_lyap(dynamics::D, jd0::V, tspan::T, q0::Vector{U},
    params::NEOParameters{T}) where {T <: Real, U <: Number, V <: Number, D}
```

Compute the Lyapunov spectrum of an orbit.

# Arguments

  * `dynamics::D`: dynamical model function.
  * `jd0::V`: initial Julian date (TDB).
  * `tspan::T`: time span of the integration [in Julian days].
  * `q0::Vector{U}`: vector of initial conditions.
  * `params::NEOParameters{T}`: see [`NEOParameters`](@ref).
