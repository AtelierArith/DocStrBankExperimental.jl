```
boundary_flux!(bc_field, heat_bc::TemperatureStateBC,
                       ::ClimaLand.TopBoundary,
                       model::EnergyHydrology,
                       Δz::ClimaCore.Fields.Field,
                       Y::ClimaCore.Fields.FieldVector,
                       p::NamedTuple,
                       t,
                       ):
```

A method of boundary fluxes which converts a state boundary condition on temperature at the top of the domain into a flux of energy.
