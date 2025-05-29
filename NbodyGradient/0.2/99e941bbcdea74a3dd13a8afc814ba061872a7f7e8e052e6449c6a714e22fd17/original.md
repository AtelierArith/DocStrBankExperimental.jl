```
CartesianIC{T<:AbstractFloat} <: InitialConditions{T}
```

Initial conditions, specified by the Cartesian coordinates and masses of each body.

# Fields

  * `x::Matrix{T}` : Positions of each body [dimension, body].
  * `v::Matrix{T}` : Velocities of each body [dimension, body].
  * `m::Vector{T}` : masses of each body.
  * `nbody::Int64` : Number of bodies in system.
  * `t0::T` : Initial time.
