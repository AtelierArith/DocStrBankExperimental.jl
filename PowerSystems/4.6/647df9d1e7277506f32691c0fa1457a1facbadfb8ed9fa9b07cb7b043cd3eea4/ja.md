```julia
clear_time_series!(sys::PowerSystems.System)

```

システムからすべての時系列データをクリアします。

HDF5ファイルに時系列データを保存している場合、これによりHDF5ファイルが削除され、新しいファイルが作成されます。

関連情報: [`remove_time_series!`](@ref remove_time_series!(sys::System, ::Type{T}) where {T <: TimeSeriesData})
