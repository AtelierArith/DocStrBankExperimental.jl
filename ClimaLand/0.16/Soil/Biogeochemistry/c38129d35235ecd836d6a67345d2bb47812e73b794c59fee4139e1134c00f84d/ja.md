```
ClimaLand.boundary_flux!(bc_field,
bc::SoilCO2StateBC,
boundary::ClimaLand.TopBoundary,
Δz::ClimaCore.Fields.Field,
Y::ClimaCore.Fields.FieldVector,
p::NamedTuple,
t,
)
```

ClimaLand.boundary_flux のメソッドで、ドメインの上部における指定された状態 BC の場合の soilco2 フラックスを返します。
