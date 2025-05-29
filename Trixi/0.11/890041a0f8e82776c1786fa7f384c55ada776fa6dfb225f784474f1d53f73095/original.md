```
flux_nonconservative_fjordholm_etal(u_ll, u_rr, orientation::Integer,
                                    equations::ShallowWaterEquations1D)
```

Non-symmetric two-point surface flux discretizing the nonconservative (source) term of that contains the gradient of the bottom topography [`ShallowWaterEquations1D`](@ref).

This flux can be used together with [`flux_fjordholm_etal`](@ref) at interfaces to ensure entropy conservation and well-balancedness.

Further details for the original finite volume formulation are available in

  * Ulrik S. Fjordholm, Siddhartha Mishra and Eitan Tadmor (2011) Well-balanced and energy stable schemes for the shallow water equations with discontinuous topography [DOI: 10.1016/j.jcp.2011.03.042](https://doi.org/10.1016/j.jcp.2011.03.042)

and for curvilinear 2D case in the paper:

  * Niklas Wintermeyer, Andrew R. Winters, Gregor J. Gassner and David A. Kopriva (2017) An entropy stable nodal discontinuous Galerkin method for the two dimensional shallow water equations on unstructured curvilinear meshes with discontinuous bathymetry [DOI: 10.1016/j.jcp.2017.03.036](https://doi.org/10.1016/j.jcp.2017.03.036)
