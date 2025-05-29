```
boundary_vars(::AtmosDrivenFluxBC, ::ClimaLand.TopBoundary)
```

An extension of the `boundary_vars` method for AtmosDrivenFluxBC. This adds the surface conditions (SHF, LHF, evaporation, and resistance) and the net radiation to the auxiliary variables.

These variables are updated in place in `soil_boundary_fluxes!`.
