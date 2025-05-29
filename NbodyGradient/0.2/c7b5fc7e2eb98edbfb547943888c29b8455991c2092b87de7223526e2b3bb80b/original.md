```
State{T<:AbstractFloat} <: AbstractState
```

Current state of simulation.

# Fields (relevant to the user)

  * `x::Matrix{T}` : Positions of each body [dimension, body].
  * `v::Matrix{T}` : Velocities of each body [dimension, body].
  * `t::Vector{T}` : Current time of simulation.
  * `m::Vector{T}` : Masses of each body.
  * `jac_step::Matrix{T}` : Current Jacobian.
  * `dqdt::Vector{T}` : Derivative with respect to time.
