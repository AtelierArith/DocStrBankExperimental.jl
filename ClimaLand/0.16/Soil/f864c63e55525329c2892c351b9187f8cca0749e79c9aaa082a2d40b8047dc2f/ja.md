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

リチャーズモデルのための所望の水量フラックスを返す境界フラックスのメソッドであり、指定された降水フラックスの場合、ドメインの上部でのものです。

`model.runoff`が`NoRunoff`型でない場合、浸透を計算する際に表面流出が考慮されます。
