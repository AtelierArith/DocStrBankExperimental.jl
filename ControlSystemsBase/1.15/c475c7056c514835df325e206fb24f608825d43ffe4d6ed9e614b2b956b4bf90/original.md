```
StateSpace{TE, T} <: AbstractStateSpace{TE}
```

An object representing a standard state space system.

See the function [`ss`](@ref) for a user facing constructor as well as the documentation page [creating systems](https://juliacontrol.github.io/ControlSystems.jl/stable/man/creating_systems/).

# Fields:

  * `A::Matrix{T}`
  * `B::Matrix{T}`
  * `C::Matrix{T}`
  * `D::Matrix{T}`
  * `timeevol::TE`
