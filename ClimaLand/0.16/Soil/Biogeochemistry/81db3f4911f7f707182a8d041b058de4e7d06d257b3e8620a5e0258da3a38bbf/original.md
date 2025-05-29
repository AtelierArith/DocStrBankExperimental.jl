```
ClimaLand.boundary_flux!(bc_field,
    bc::SoilCO2FluxBC,
    boundary::ClimaLand.AbstractBoundary,
    Δz::ClimaCore.Fields.Field,
    Y::ClimaCore.Fields.FieldVector,
    p::NamedTuple,
    t,
)
```

A method of ClimaLand.boundary_flux which updates the soilco2 flux (kg CO2 /m^2/s) in the case of a prescribed flux BC at either the top or bottom of the domain.
