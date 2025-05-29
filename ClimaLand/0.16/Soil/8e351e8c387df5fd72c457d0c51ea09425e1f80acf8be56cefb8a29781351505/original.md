```
boundary_flux!(bc_field, bc::FreeDrainage,
                       boundary::ClimaLand.BottomBoundary,
                       model::AbstractSoilModel,
                       Δz::ClimaCore.Fields.Field,
                       Y::ClimaCore.Fields.FieldVector,
                       p::NamedTuple,
                       t,
                       )
```

A method of boundary fluxes which enforces free drainage at the bottom of the domain.
