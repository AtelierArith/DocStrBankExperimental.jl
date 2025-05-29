```
flux_nonconservative_central(u_ll, u_rr, orientation::Integer,
                             equations::IdealGlmMhdMultiIonEquations2D)
```

Central non-conservative two-point "flux", where the symmetric parts are computed with standard averages. The use of this term together with [`flux_central`](@ref)  with [`VolumeIntegralFluxDifferencing`](@ref) yields a "standard" (weak-form) DGSEM discretization of the multi-ion GLM-MHD system. This flux can also be used to construct a standard local Lax-Friedrichs flux using `surface_flux = (flux_lax_friedrichs, flux_nonconservative_central)`.

!!! info "Usage and Scaling of Non-Conservative Fluxes in Trixi"
    The central non-conservative fluxes implemented in this function are written as the product of local and symmetric parts, where the symmetric part is a standard average. These fluxes are meant to be used in the same way as the conservative fluxes (i.e., flux + flux_noncons  in both volume and surface integrals). In this routine, the fluxes are multiplied by 2 because  the non-conservative fluxes are always multiplied by 0.5 whenever they are used in the Trixi code.


The term is composed of four individual non-conservative terms:

1. The Godunov-Powell term, which arises for plasmas with non-vanishing magnetic field divergence, and is evaluated as a function of the charge-averaged velocity.
2. The Lorentz-force term, which becomes a conservative term in the limit of one ion species for vanishing electron pressure gradients.
3. The "multi-ion" term, which vanishes in the limit of one ion species.
4. The GLM term, which is needed for Galilean invariance.
