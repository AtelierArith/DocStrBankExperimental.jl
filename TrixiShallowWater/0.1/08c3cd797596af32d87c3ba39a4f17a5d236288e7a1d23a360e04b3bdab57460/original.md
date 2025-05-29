```
hydrostatic_reconstruction_chen_noelle(u_ll, u_rr, orientation::Integer,
                                       equations::ShallowWaterEquationsWetDry1D)
```

A particular type of hydrostatic reconstruction of the water height to guarantee well-balancedness for a general bottom topography of the [`ShallowWaterEquationsWetDry1D`](@ref). The reconstructed solution states `u_ll_star` and `u_rr_star` variables are used to evaluate the surface numerical flux at the interface. The key idea is a linear reconstruction of the bottom and water height at the interfaces using subcells. Use in combination with the generic numerical flux routine [`Trixi.FluxHydrostaticReconstruction`](@extref).

Further details on this hydrostatic reconstruction and its motivation can be found in

  * Guoxian Chen and Sebastian Noelle (2017) A new hydrostatic reconstruction scheme based on subcell reconstructions [DOI:10.1137/15M1053074](https://dx.doi.org/10.1137/15M1053074)
