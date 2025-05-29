```
flux_ersing_etal(u_ll, u_rr, orientation::Integer,
                                 equations::ShallowWaterMultiLayerEquations1D)
```

Entropy conservative split form, without the hydrostatic pressure. This flux should be used together with the nonconservative [`flux_nonconservative_ersing_etal`](@ref) to create a scheme that is entropy conservative and well-balanced.

To obtain an entropy stable formulation the `surface_flux` can be set as `FluxPlusDissipation(flux_ersing_etal, DissipationLocalLaxFriedrichs()), flux_nonconservative_ersing_etal`.
