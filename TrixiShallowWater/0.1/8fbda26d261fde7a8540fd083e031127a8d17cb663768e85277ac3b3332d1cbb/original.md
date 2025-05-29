```
flux_ersing_etal(u_ll, u_rr, orientation::Integer,
                                 equations::ShallowWaterMultiLayerEquations1D)
```

Total energy conservative (mathematical entropy for MLSWE) split form, without the hydrostatic pressure. When the bottom topography is nonzero this scheme will be well-balanced when used with the  nonconservative [`flux_nonconservative_ersing_etal`](@ref).

To obtain an entropy stable formulation the `surface_flux` can be set as `FluxPlusDissipation(flux_ersing_etal, DissipationLocalLaxFriedrichs()), flux_nonconservative_ersing_etal`.

In the two-layer setting this combination is equivalent to the fluxes in:

  * Patrick Ersing, Andrew R. Winters (2023) An entropy stable discontinuous Galerkin method for the two-layer shallow water equations on  curvilinear meshes [DOI: 10.1007/s10915-024-02451-2](https://doi.org/10.1007/s10915-024-02451-2)
