```julia
struct ToDeviceArray{T} <: XRT.AbstractSyncDirectionArray{T}
```

`Array`をラップするデータ型で、[`XRT.sync!`](@ref)関数を呼び出す際に単一の同期方向を禁止します。[`@prepare_bitstream`](@ref)マクロによって作成された関数で使用できます。代わりに、[`XRT.ToDeviceWrapper`](@ref)または[`XRT.FromDeviceWrapper`](@ref)を使用してください。
