```julia
has_service(
    device::PowerSystems.Device,
    _::Type{T<:PowerSystems.Service}
) -> Bool

```

デバイスにタイプ T のサービスが接続されている場合は true を返します。
