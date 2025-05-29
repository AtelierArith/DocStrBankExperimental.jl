```
flux_nonconservative_audusse_etal(u_ll, u_rr, orientation::Integer,
                                  equations::ShallowWaterEquations1D)
```

Non-symmetric two-point surface flux that discretizes the nonconservative (source) term. The discretization uses the `hydrostatic_reconstruction_audusse_etal` on the conservative variables.

This hydrostatic reconstruction ensures that the finite volume numerical fluxes remain well-balanced for discontinuous bottom topographies [`ShallowWaterEquations1D`](@ref). Should be used together with [`FluxHydrostaticReconstruction`](@ref) and [`hydrostatic_reconstruction_audusse_etal`](@ref) in the surface flux to ensure consistency.

Further details on the hydrostatic reconstruction and its motivation can be found in

  * Emmanuel Audusse, François Bouchut, Marie-Odile Bristeau, Rupert Klein, and Benoit Perthame (2004) A fast and stable well-balanced scheme with hydrostatic reconstruction for shallow water flows [DOI: 10.1137/S1064827503431090](https://doi.org/10.1137/S1064827503431090)
