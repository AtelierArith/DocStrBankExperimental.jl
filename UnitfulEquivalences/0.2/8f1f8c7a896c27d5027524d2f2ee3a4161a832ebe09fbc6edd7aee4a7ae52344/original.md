```
@eqrelation Name a/b = c
@eqrelation Name a*b = c
```

Add a proportional or antiproportional relation between dimensions `a` and `b` to an existing equivalence type `Name <: Equivalence`. The dimensions `a` and `b` must be specified as quantity type aliases like `Unitful.Energy`.

# Example

```@julia
using Unitful: Energy, Mass, c0
struct MassEnergy <: Equivalence end
@eqrelation MassEnergy Energy/Mass = c0^2
```

In the rest frame of a particle, its energy is proportional to its mass. Defining the `MassEnergy` equivalence like above allows conversion between energies and masses via `uconvert(massunit, energy, MassEnergy())` and `uconvert(energyunit, massunit, MassEnergy())`.
