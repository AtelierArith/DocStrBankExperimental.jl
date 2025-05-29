```
SimpleLiquid{dims, ...} <: System
```

Holds information about a homogeneous, isotropic system with radially symmetric pair interactions. `dims` is the dimensionality.

Construct using

`SimpleLiquid(dims, ρ, kBT, potential)`

Fields:

  * ρ: number density, must be either a `Number` in case of a single component system, or a `Vector` in case of a mixture. In the latter case, each element contains the number density of the respective component.
  * kBT: thermal energy
  * potential::Potential: the interaction potential.

Examples:

```julia
ρ = 0.5; kBT = 1.1; dims = 3
pot = SingleComponentHardSpheres()
system = SimpleLiquid(dims, ρ, kBT, pot)
```

```julia
ρ = [0.5, 0.1]; kBT = 5.2; dims = 3
pot = MultiComponentHardSpheres([1.0, 0.8])
system = SimpleLiquid(dims, ρ, kBT, pot)
```
