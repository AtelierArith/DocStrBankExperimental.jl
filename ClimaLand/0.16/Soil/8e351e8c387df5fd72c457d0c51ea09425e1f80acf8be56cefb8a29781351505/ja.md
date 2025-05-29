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

ドメインの底で自由排水を強制する境界フラックスのメソッド。
