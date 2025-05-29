```
gauss_method(obs::Vector{RadecMPC{T}}, params::NEOParameters{T}) where {T <: Real}
gauss_method(observatories::Vector{ObservatoryMPC{T}}, dates::Vector{DateTime},
    α::Vector{U}, δ::Vector{U}, params::NEOParameters{T}) where {T <: Real, U <: Number}
```

Core Gauss method of Initial Orbit determination (IOD).

## Arguments

  * `obs::Vector{RadecMPC{T}}`: three observations.
  * `observatories::Vector{ObservatoryMPC{T}}`: sites of observation.
  * `dates::Vector{DateTime}`: times of observation.
  * `α::Vector{U}`: right ascension [rad].
  * `δ::Vector{U}`: declination [rad].
  * `params::NEOParameters{T}`: see `Gauss Method Parameters` of [`NEOParameters`](@ref).

!!! reference
    See Algorithm 5.5 in page 274 https://doi.org/10.1016/C2016-0-02107-1.

