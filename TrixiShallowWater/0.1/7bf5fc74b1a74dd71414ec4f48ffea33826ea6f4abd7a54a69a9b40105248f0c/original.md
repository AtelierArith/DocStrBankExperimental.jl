```
flux_nonconservative_ersing_etal(u_ll, u_rr, orientation::Integer,
                                 equations::ShallowWaterTwoLayerEquations1D)
```

Non-symmetric path-conservative two-point flux discretizing the nonconservative (source) term that contains the gradients of the bottom topography and waterheights from the coupling between layers and the nonconservative pressure formulation [`ShallowWaterMultiLayerEquations1D`](@ref).

When the bottom topography is nonzero this scheme will be well-balanced when used with [`flux_ersing_etal`](@ref).

In the two-layer setting this combination is equivalent to the fluxes in:

  * Patrick Ersing, Andrew R. Winters (2023) An entropy stable discontinuous Galerkin method for the two-layer shallow water equations on  curvilinear meshes [DOI: 10.1007/s10915-024-02451-2](https://doi.org/10.1007/s10915-024-02451-2)
