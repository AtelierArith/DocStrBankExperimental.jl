```
function ClimaLand.turbulent_fluxes!(
    dest,
    atmos::PrescribedAtmosphere,
    model::CanopyModel,
    Y::ClimaCore.Fields.FieldVector,
    p::NamedTuple,
    t,
)
```

A canopy specific function for compute turbulent fluxes with the atmosphere; returns the latent heat flux, sensible heat flux, vapor flux, and aerodynamic resistance.

We cannot use the default version in src/shared_utilities/drivers.jl because the canopy requires a different resistance for vapor and sensible heat fluxes, and the resistances depend on ustar, which we must compute using SurfaceFluxes before adjusting to account for these resistances.
