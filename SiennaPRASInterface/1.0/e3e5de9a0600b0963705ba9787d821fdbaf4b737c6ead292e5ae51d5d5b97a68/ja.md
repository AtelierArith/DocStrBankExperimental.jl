```julia
DeviceRAModel(
    ::Type{D<:PowerSystems.Device},
    ::Type{B<:SiennaPRASInterface.AbstractRAFormulation};
    time_series_names,
    kwargs...
) -> SiennaPRASInterface.DeviceRAModel

```

# 引数

  * `::Type{D}`: デバイスタイプ
  * `::Type{B}`: 定式化タイプ
  * `time_series_names::Dict{Symbol, String}`: 時系列 `Symbol` から名前へのマッピング
  * `kwargs...`: 定式化コンストラクタに渡す追加の引数

DeviceRAModelのキーワード引数は定式化コンストラクタに渡されます。

`time_series_names` Dictを渡して、時系列 `Symbol` から名前へのマッピングを行うこともできます。

# 例

```julia
DeviceRAModel(
    PSY.Generator,
    GeneratorPRAS(max_active_power="max_active_power"),
)
```

```julia
DeviceRAModel(
    PSY.HydroEnergyReservoir,
    HydroEnergyReservoirPRAS;
    max_active_power="max_active_power",
    inflow="inflow",
    storage_capacity="storage_capacity",
)
```

```julia
DeviceRAModel(
    PSY.HybridSystem,
    HybridSystemPRAS;
    time_series_names=Dict(:max_active_power="max_active_power"),
)
```
