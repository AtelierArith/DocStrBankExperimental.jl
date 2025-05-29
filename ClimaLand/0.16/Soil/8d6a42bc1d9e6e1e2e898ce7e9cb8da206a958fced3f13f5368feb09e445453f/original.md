```
boundary_var_types(
    ::EnergyHydrology{FT},
    ::AtmosDrivenFluxBC{<:CoupledAtmosphere, <:CoupledRadiativeFluxes},
    ::ClimaLand.TopBoundary,
) where {FT}
```

An extension of the `boundary_var_types` method for AtmosDrivenFluxBC with coupled atmosphere and radiative fluxes. This specifies the type of the additional variables.

This method includes additional fluxes needed by the atmosphere: momentum fluxes (`ρτxz`, `ρτyz`) and the buoyancy flux (`buoy_flux`). These are updated in place when the coupler computes turbulent fluxes, rather than in `soil_boundary_fluxes!`.

Note that we currently store these in the land model because the coupler computes turbulent land/atmosphere fluxes using ClimaLand functions, and the land model needs to be able to store the fluxes as an intermediary. Once we compute fluxes entirely within the coupler, we can remove this.
