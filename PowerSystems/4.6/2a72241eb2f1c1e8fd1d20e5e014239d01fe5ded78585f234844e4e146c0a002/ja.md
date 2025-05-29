```julia
PowerModelsData(
    file::Union{IO, String};
    kwargs...
) -> PowerSystems.PowerModelsData

```

生のファイルからPowerModelsDataを構築します。現在、PowerModelsによって解析されたMATPOWERおよびPSSEデータファイルをサポートしています。
