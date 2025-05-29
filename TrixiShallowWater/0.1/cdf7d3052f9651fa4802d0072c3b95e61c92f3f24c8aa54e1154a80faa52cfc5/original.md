```
flux_nonconservative_chen_noelle(u_ll, u_rr,
                                 orientation::Integer,
                                 equations::ShallowWaterEquationsWetDry1D)
```

Non-symmetric two-point surface flux that discretizes the nonconservative (source) term. The discretization uses the [`hydrostatic_reconstruction_chen_noelle`](@ref) on the conservative variables.

Should be used together with [`Trixi.FluxHydrostaticReconstruction`](@extref) and [`hydrostatic_reconstruction_chen_noelle`](@ref) in the surface flux to ensure consistency.

Further details on the hydrostatic reconstruction and its motivation can be found in

  * Guoxian Chen and Sebastian Noelle (2017) A new hydrostatic reconstruction scheme based on subcell reconstructions [DOI:10.1137/15M1053074](https://dx.doi.org/10.1137/15M1053074)
