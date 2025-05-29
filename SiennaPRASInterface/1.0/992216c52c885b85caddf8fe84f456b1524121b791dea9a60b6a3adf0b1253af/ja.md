# 引数

  * `aggregation::Type{T} where T<:PowerSystems.AggregationTopology`: PRAS地域に使用する集約のレベル
  * `device_models::Array{SiennaPRASInterface.DeviceRAModel}`: コンポーネントをPRASに変換するためのDeviceRAModels

RATemplateは、PowerSystems.jlシステムからPRASシミュレーションを構築するために必要なすべての構成を含んでいます。

PRASはエリアベースのモデルであるため、適用する集約のレベルを提供します。

PRASモデルは逆順で処理され、後のモデルが優先されます。

# 例

```julia
template = RATemplate(
    PSY.Area,
    [
        DeviceRAModel(
            PSY.Generator,
            GeneratorPRAS(max_active_power="max_active_power"),
        ),
        DeviceRAModel(
            PSY.HydroEnergyReservoir,
            HydroEnergyReservoirPRAS(
                max_active_power="max_active_power",
                inflow="inflow",
                storage_capacity="storage_capacity",
            ),
        ),
    ],
)
```
