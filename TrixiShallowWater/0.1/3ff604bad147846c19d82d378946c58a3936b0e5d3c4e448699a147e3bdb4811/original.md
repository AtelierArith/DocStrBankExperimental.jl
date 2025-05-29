```
hydrostatic_reconstruction_ersing_etal(u_ll, u_rr, equations::ShallowWaterMultiLayerEquations2D)
```

A particular type of hydrostatic reconstruction of the water height and bottom topography to  guarantee well-balancedness in the presence of wet/dry transitions and entropy stability for the  [`ShallowWaterMultiLayerEquations2D`](@ref).  The reconstructed solution states `u_ll_star` and `u_rr_star` variables are used to evaluate the  surface numerical flux at the interface. The key idea is a piecewise linear reconstruction of the  bottom topography and water height interfaces using subcells, where the bottom topography is allowed  to be discontinuous.  Use in combination with the generic numerical flux routine [`Trixi.FluxHydrostaticReconstruction`](@extref).
