```
turbulent_fluxes!(dest,
                  atmos::PrescribedAtmosphere,
                  model::AbstractModel,
                  Y::ClimaCore.Fields.FieldVector,
                  p::NamedTuple,
                  t
                  )
```

Computes the turbulent surface flux terms at the ground for a standalone simulation, including turbulent energy fluxes as well as the water vapor flux (in units of m^3/m^2/s of water). Positive fluxes indicate flow from the ground to the atmosphere.

It solves for these given atmospheric conditions, stored in `atmos`, model parameters, and the surface conditions.
