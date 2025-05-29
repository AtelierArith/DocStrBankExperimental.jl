```
flux_ruedaramirez_etal(u_ll, u_rr, orientation, equations::IdealGlmMhdMultiIonEquations3D)
```

多イオンGLM-MHD方程式のためのエントロピー保存二点フラックスは以下から得られます。

  * A. Rueda-Ramírez, A. Sikstel, G. Gassner, An Entropy-Stable Discontinuous Galerkin Discretization of the Ideal Multi-Ion Magnetohydrodynamics System (2024). Journal of Computational Physics. [DOI: 10.1016/j.jcp.2024.113655](https://doi.org/10.1016/j.jcp.2024.113655).

このフラックス（MHD非保存項と共に）は、1つのイオン種の場合において、以下のフラックスと整合しています：

  * Derigs et al. (2018). Ideal GLM-MHD: About the entropy consistent nine-wave magnetic field divergence diminishing ideal magnetohydrodynamics equations for multi-ion [DOI: 10.1016/j.jcp.2018.03.002](https://doi.org/10.1016/j.jcp.2018.03.002)
