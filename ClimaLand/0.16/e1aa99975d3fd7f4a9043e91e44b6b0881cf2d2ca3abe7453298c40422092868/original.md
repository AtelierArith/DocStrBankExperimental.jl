```
function ClimaLand.boundary_flux!(bc_field,
    bc::RunoffBC,
    ::TopBoundary,
    model::Soil.RichardsModel,
    Δz::FT,
    Y::ClimaCore.Fields.FieldVector,
    p::NamedTuple,
    t,
    params,
)
```

Extension of the `ClimaLand.boundary_flux` function, which returns the water volume boundary flux for the soil. At the top boundary, return the soil infiltration (computed each step and stored in `p.soil_infiltration`).
