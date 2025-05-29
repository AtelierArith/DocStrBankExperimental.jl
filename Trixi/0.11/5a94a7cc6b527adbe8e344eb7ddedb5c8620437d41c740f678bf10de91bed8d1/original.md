```
flux_nonconservative_ruedaramirez_etal(u_ll, u_rr,
                                       orientation_or_normal_direction,
                                       equations::IdealGlmMhdMultiIonEquations3D)
```

Entropy-conserving non-conservative two-point "flux" as described in 

  * A. Rueda-Ramírez, A. Sikstel, G. Gassner, An Entropy-Stable Discontinuous Galerkin Discretization of the Ideal Multi-Ion Magnetohydrodynamics System (2024). Journal of Computational Physics. [DOI: 10.1016/j.jcp.2024.113655](https://doi.org/10.1016/j.jcp.2024.113655).

!!! info "Usage and Scaling of Non-Conservative Fluxes in Trixi.jl"
    The non-conservative fluxes derived in the reference above are written as the product of local and symmetric parts and are meant to be used in the same way as the conservative fluxes (i.e., flux + flux_noncons in both volume and surface integrals). In this routine,  the fluxes are multiplied by 2 because the non-conservative fluxes are always multiplied  by 0.5 whenever they are used in the Trixi.jl code.


The term is composed of four individual non-conservative terms:

1. The Godunov-Powell term, which arises for plasmas with non-vanishing magnetic field divergence, and is evaluated as a function of the charge-averaged velocity.
2. The Lorentz-force term, which becomes a conservative term in the limit of one ion species for vanishing electron pressure gradients.
3. The "multi-ion" term, which vanishes in the limit of one ion species.
4. The GLM term, which is needed for Galilean invariance.
