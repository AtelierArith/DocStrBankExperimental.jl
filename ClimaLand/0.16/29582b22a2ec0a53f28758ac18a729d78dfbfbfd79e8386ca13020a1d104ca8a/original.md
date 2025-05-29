```
net_radiation!(dest::ClimaCore.Fields.Field,
               radiation::PrescribedRadiativeFluxes{FT},
               model::AbstractModel{FT},
               Y::ClimaCore.Fields.FieldVector,
               p::NamedTuple,
               t,
               ) where {FT}
```

Computes net radiative  fluxes for a prescribed incoming  longwave and shortwave radiation.
