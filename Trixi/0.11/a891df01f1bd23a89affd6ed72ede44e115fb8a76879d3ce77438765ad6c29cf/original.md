```
flux_wintermeyer_etal(u_ll, u_rr, orientation,
                      equations::ShallowWaterEquations1D)
```

Total energy conservative (mathematical entropy for shallow water equations) split form. When the bottom topography is nonzero this scheme will be well-balanced when used as a `volume_flux`. For the `surface_flux` either [`flux_wintermeyer_etal`](@ref) or [`flux_fjordholm_etal`](@ref) can be used to ensure well-balancedness and entropy conservation.

Further details are available in Theorem 1 of the paper:

  * Niklas Wintermeyer, Andrew R. Winters, Gregor J. Gassner and David A. Kopriva (2017) An entropy stable nodal discontinuous Galerkin method for the two dimensional shallow water equations on unstructured curvilinear meshes with discontinuous bathymetry [DOI: 10.1016/j.jcp.2017.03.036](https://doi.org/10.1016/j.jcp.2017.03.036)
