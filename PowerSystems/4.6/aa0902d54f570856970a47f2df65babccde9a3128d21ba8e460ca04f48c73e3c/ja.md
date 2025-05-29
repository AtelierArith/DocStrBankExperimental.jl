```julia
remove_time_series!(
    sys::PowerSystems.System,
    _::Type{T<:InfrastructureSystems.TimeSeriesData}
)

```

指定された時間系列タイプのすべての時間系列データを削除します。

関連情報: [`clear_time_series!`](@ref)

HDF5ファイルに時間系列データを保存している場合、`remove_time_series!`は実際にはファイルスペースを解放しません（HDF5の動作）。すべてまたはほとんどの時間系列インスタンスを削除したい場合は、`clear_time_series!`の使用を検討してください。これにより、HDF5ファイルが削除され、新しいファイルが作成されます。PowerSystemsはこの種のワークフローを自動化する計画を持っています。
