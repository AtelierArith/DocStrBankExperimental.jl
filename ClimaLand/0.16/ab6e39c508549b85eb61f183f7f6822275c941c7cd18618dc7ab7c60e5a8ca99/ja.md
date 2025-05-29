```
turbulent_fluxes!(dest,
                  atmos::PrescribedAtmosphere,
                  model::AbstractModel,
                  Y::ClimaCore.Fields.FieldVector,
                  p::NamedTuple,
                  t
                  )
```

地上での独立したシミュレーションのために、乱流表面フラックス項を計算します。これには、乱流エネルギーフラックスと水蒸気フラックス（単位は水のm^3/m^2/s）が含まれます。正のフラックスは、地面から大気への流れを示します。

これは、`atmos`に格納された大気条件、モデルパラメータ、および表面条件に基づいて解決されます。
