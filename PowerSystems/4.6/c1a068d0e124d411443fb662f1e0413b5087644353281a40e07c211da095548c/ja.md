```julia
remove_service!(
    device::PowerSystems.Device,
    service::PowerSystems.Service
)

```

デバイスからサービスを削除します。

サービスがデバイスに接続されていない場合、ArgumentErrorをスローします。
