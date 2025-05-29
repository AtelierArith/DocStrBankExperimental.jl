```
AbstractOutPhaseSpaceLayout{IN_PSL<:AbstractInPhaseSpaceLayout} <: AbstractPhaseSpaceLayout
```

The `AbstractOutPhaseSpaceLayout` represents the phase space layout for the outgoing particles in a scattering process. It typically depends on the phase space layout of the incoming particles and specifies how the momenta of the outgoing particles are constructed from the respective coordinates.

The generic parameter `IN_PSL` links the outgoing phase space layout to the incoming layout, allowing consistency between the two configurations in the process.

## Interface Functions to Implement:

  * `phase_space_dimension(proc, model, layout::AbstractOutPhaseSpaceLayout)`: Defines the   number of independent phase space coordinates for the outgoing particles.
  * `in_phase_space_layout(out_psl::AbstractOutPhaseSpaceLayout)`: Provides the associated   incoming phase space layout to ensure consistency between incoming and outgoing configurations.
  * `_build_momenta(proc, model, Ptot::AbstractFourMomentum, out_psl::AbstractOutPhaseSpaceLayout, out_coords::Tuple)`:   Constructs the momenta for the outgoing particles, ensuring they comply with energy and momentum conservation based on the total incoming four-momentum.
