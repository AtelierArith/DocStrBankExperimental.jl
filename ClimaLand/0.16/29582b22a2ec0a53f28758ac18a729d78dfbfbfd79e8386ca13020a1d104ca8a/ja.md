```
net_radiation!(dest::ClimaCore.Fields.Field,
               radiation::PrescribedRadiativeFluxes{FT},
               model::AbstractModel{FT},
               Y::ClimaCore.Fields.FieldVector,
               p::NamedTuple,
               t,
               ) where {FT}
```

指定された入射長波および短波放射に対するネット放射フラックスを計算します。
