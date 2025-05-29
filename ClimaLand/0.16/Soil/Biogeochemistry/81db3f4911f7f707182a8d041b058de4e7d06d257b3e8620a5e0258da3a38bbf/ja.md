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

ClimaLand.boundary_flux のメソッドで、領域の上部または下部で指定されたフラックス BC の場合に土壌 CO2 フラックス (kg CO2 /m^2/s) を更新します。
