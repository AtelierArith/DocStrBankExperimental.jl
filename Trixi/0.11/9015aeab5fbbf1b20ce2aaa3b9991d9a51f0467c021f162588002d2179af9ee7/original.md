```
VolumeIntegralShockCapturingHG(indicator; volume_flux_dg=flux_central,
                                          volume_flux_fv=flux_lax_friedrichs)
```

Shock-capturing volume integral type for DG methods using a convex blending of the finite volume method with numerical flux `volume_flux_fv` and the [`VolumeIntegralFluxDifferencing`](@ref) with volume flux `volume_flux_dg`. The amount of blending is determined by the `indicator`, e.g., [`IndicatorHennemannGassner`](@ref).

## References

  * Hennemann, Gassner (2020) "A provably entropy stable subcell shock capturing approach for high order split form DG" [arXiv: 2008.12044](https://arxiv.org/abs/2008.12044)
