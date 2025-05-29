```
boundary_flux!(bc_field, heat_bc::TemperatureStateBC,
                       ::ClimaLand.BottomBoundary,
                       model::EnergyHydrology,
                       Δz::ClimaCore.Fields.Field,
                       Y::ClimaCore.Fields.FieldVector,
                       p::NamedTuple,
                       t,
                       )
```

A method of boundary fluxes which converts a state boundary condition on temperature at the bottom of the domain into a flux of energy.
