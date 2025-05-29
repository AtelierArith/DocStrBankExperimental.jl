```
MassEnergy()
```

Equivalence to convert between mass and energy according to the relation $E = mc^2$, where

  * $E$ is the energy,
  * $m$ is the mass and
  * $c$ is the speed of light in vacuum.

# Example

```jldoctest
julia> uconvert(u"keV", 1u"me", MassEnergy()) # electron rest mass is equivalent to ≈511 keV
510.9989499961642 keV
```
