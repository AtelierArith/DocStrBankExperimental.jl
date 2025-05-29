```
hydrostatic_reconstruction_audusse_etal(u_ll, u_rr, orientation::Integer,
                                        equations::ShallowWaterEquations1D)
```

A particular type of hydrostatic reconstruction on the water height to guarantee well-balancedness for a general bottom topography [`ShallowWaterEquations1D`](@ref). The reconstructed solution states `u_ll_star` and `u_rr_star` variables are then used to evaluate the surface numerical flux at the interface. Use in combination with the generic numerical flux routine [`FluxHydrostaticReconstruction`](@ref).

Further details on this hydrostatic reconstruction and its motivation can be found in

  * Emmanuel Audusse, François Bouchut, Marie-Odile Bristeau, Rupert Klein, and Benoit Perthame (2004) A fast and stable well-balanced scheme with hydrostatic reconstruction for shallow water flows [DOI: 10.1137/S1064827503431090](https://doi.org/10.1137/S1064827503431090)
