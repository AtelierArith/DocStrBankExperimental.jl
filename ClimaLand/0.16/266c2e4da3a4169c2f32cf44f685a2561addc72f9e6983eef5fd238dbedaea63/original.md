```
CoupledAtmosphere{FT} <: AbstractAtmosphericDrivers{FT}
```

To be used when coupling to an atmosphere model. Contains fields that are used to compute surface fluxes in the coupled setup.

When constructed without a space, the struct doesn't contain anything, but it still acts as a flag that fluxes have been updated by the coupler and don't need to be recomputed. When constructed with a space, the struct contains the fields needed to compute surface fluxes in the coupled setup, which are accessed by ClimaCoupler.
