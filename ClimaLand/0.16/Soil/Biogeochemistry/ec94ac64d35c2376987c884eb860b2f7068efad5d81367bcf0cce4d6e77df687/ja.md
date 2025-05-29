```
ClimaLand.boundary_flux!(bc_field,
bc::AtmosCO2StateBC,
boundary::ClimaLand.TopBoundary,
Δz::ClimaCore.Fields.Field,
Y::ClimaCore.Fields.FieldVector,
p::NamedTuple,
t,
)
```

ClimaLand.boundary_flux のメソッドで、領域の上部で大気中の CO2 が使用される場合の soilco2 フラックスを返します。
