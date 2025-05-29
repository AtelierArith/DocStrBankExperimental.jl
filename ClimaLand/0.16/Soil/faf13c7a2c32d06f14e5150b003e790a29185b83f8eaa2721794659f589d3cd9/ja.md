```
boundary_flux!(bc_field, heat_bc::TemperatureStateBC,
                       ::ClimaLand.TopBoundary,
                       model::EnergyHydrology,
                       Δz::ClimaCore.Fields.Field,
                       Y::ClimaCore.Fields.FieldVector,
                       p::NamedTuple,
                       t,
                       ):
```

ドメインの上部における温度の状態境界条件をエネルギーのフラックスに変換する境界フラックスのメソッド。
