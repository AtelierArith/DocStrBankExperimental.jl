```julia
generate_pras_system(
    sys::PowerSystems.System,
    template::SiennaPRASInterface.RATemplate
) -> PRASCore.Systems.SystemModel{_A, _B, T, PRASCore.Systems.MW, PRASCore.Systems.MWh} where {_A, _B, T<:Dates.Period}
generate_pras_system(
    sys::PowerSystems.System,
    template::SiennaPRASInterface.RATemplate,
    export_location::Union{Nothing, String}
) -> PRASCore.Systems.SystemModel{_A, _B, T, PRASCore.Systems.MW, PRASCore.Systems.MWh} where {_A, _B, T<:Dates.Period}

```

SiennaシステムからPRASシステムを作成するためにRATemplateを使用します。

# 引数

  * `sys::PSY.System`: Sienna PowerSystemsシステム
  * `template::RATemplate`: RATemplate
  * `export_location::Union{Nothing, String}`: PRAS SystemModelのエクスポート先

# 戻り値

  * `PRASCore.SystemModel`: PRAS SystemModel

# 例

```julia
generate_pras_system(sys, template)
```

元のシステムはNATURAL_UNITSにのみ設定されることに注意してください。
