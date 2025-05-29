```
boundary_flux!(bc_field, heat_bc::TemperatureStateBC,
                       ::ClimaLand.BottomBoundary,
                       model::EnergyHydrology,
                       Δz::ClimaCore.Fields.Field,
                       Y::ClimaCore.Fields.FieldVector,
                       p::NamedTuple,
                       t,
                       )
```

ドメインの底における温度の状態境界条件をエネルギーのフラックスに変換する境界フラックスのメソッド。
