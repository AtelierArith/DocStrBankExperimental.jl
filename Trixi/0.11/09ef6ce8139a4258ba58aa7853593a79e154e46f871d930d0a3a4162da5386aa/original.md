```
flux_ruedaramirez_etal(u_ll, u_rr, orientation, equations::IdealGlmMhdMultiIonEquations3D)
```

Entropy conserving two-point flux for the multi-ion GLM-MHD equations from

  * A. Rueda-Ramírez, A. Sikstel, G. Gassner, An Entropy-Stable Discontinuous Galerkin Discretization of the Ideal Multi-Ion Magnetohydrodynamics System (2024). Journal of Computational Physics. [DOI: 10.1016/j.jcp.2024.113655](https://doi.org/10.1016/j.jcp.2024.113655).

This flux (together with the MHD non-conservative term) is consistent in the case of one ion species with the flux of:

  * Derigs et al. (2018). Ideal GLM-MHD: About the entropy consistent nine-wave magnetic field divergence diminishing ideal magnetohydrodynamics equations for multi-ion [DOI: 10.1016/j.jcp.2018.03.002](https://doi.org/10.1016/j.jcp.2018.03.002)
