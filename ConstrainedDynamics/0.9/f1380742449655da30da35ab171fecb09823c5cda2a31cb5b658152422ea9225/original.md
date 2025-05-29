```julia
mutable struct Mechanism{T, Nn, Ne, Nb, Nf, Ni} <: ConstrainedDynamics.AbstractMechanism{T, Nn, Ne, Nb, Nf, Ni}
```

A `Mechanism` contains the [`Origin`](@ref), [`Body`](@ref)s, and [`EqualityConstraint`](@ref)s of a system and can be used for simulation.

# Important attributes

  * `origin`:        The origin of a mechanism.
  * `bodies`:        The bodies of a mechanism (Dict).
  * `eqconstraints`: The equality constraints (joints) of a mechanism (Dict).
  * `Δt`:            The time step of the mechanism.
  * `g`:             The gravitational acceleration in z-direction.

# Constuctors

```
Mechanism(origin, bodies; Δt, g)
Mechanism(origin, bodies, eqcs; Δt, g)
Mechanism(urdf_filename; floating, Δt, g)
```
