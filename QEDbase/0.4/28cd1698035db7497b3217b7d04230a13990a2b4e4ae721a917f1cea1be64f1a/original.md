```
AbstractInPhaseSpaceLayout <: AbstractPhaseSpaceLayout
```

The `AbstractInPhaseSpaceLayout` represents the phase space layout for the incoming particles in a scattering process. It defines the way in which the momenta of incoming particles are constructed from phase space coordinates.

## Interface Functions to Implement:

  * `phase_space_dimension(proc, model, layout::AbstractInPhaseSpaceLayout)`: Defines the number   of independent phase space coordinates for the incoming particles.
  * `_build_momenta(proc, model, in_psl::AbstractInPhaseSpaceLayout, in_coords::Tuple)`: Constructs   the momenta for the incoming particles using the phase space coordinates.
