```
boundary_flux!(bc_field, bc::RichardsAtmosDrivenFluxBC,
                       boundary::ClimaLand.AbstractBoundary,
                       model::RichardsModel{FT},
                       Δz::ClimaCore.Fields.Field,
                       Y::ClimaCore.Fields.FieldVector,
                       p::NamedTuple,
                       t,
                       ) where {FT}
```

A method of boundary fluxes which returns the desired water volume flux for the RichardsModel, at the top of the domain, in the case of a prescribed precipitation flux.

If `model.runoff` is not of type `NoRunoff`, surface runoff is accounted for when computing the infiltration.
