```
flux_nonconservative_wintermeyer_etal(u_ll, u_rr, orientation::Integer,
                                      equations::ShallowWaterEquations2D)
flux_nonconservative_wintermeyer_etal(u_ll, u_rr,
                                      normal_direction::AbstractVector,
                                      equations::ShallowWaterEquations2D)
```

Non-symmetric two-point volume flux discretizing the nonconservative (source) term that contains the gradient of the bottom topography [`ShallowWaterEquations2D`](@ref).

For the `surface_flux` either [`flux_wintermeyer_etal`](@ref) or [`flux_fjordholm_etal`](@ref) can be used to ensure well-balancedness and entropy conservation.

Further details are available in the papers:

  * Niklas Wintermeyer, Andrew R. Winters, Gregor J. Gassner and David A. Kopriva (2017) An entropy stable nodal discontinuous Galerkin method for the two dimensional shallow water equations on unstructured curvilinear meshes with discontinuous bathymetry [DOI: 10.1016/j.jcp.2017.03.036](https://doi.org/10.1016/j.jcp.2017.03.036)
  * Patrick Ersing, Andrew R. Winters (2023) An entropy stable discontinuous Galerkin method for the two-layer shallow water equations on curvilinear meshes [DOI: 10.48550/arXiv.2306.12699](https://doi.org/10.48550/arXiv.2306.12699)
