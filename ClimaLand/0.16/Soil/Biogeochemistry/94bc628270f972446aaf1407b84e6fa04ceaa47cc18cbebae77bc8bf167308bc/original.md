```
ClimaLand.boundary_flux!(bc_field,
    bc::SoilCO2StateBC,
    boundary::ClimaLand.BottomBoundary,
    Δz::ClimaCore.Fields.Field,
    Y::ClimaCore.Fields.FieldVector,
    p::NamedTuple,
    t,
)
```

A method of ClimaLand.boundary_flux which returns the soilco2 flux in the case of a prescribed state BC at bottom of the domain.
