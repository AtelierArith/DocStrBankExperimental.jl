```julia
add_service!(
    device::PowerSystems.Device,
    service::PowerSystems.Service,
    sys::PowerSystems.System
)

```

[`add_service!`](@ref)と似ていますが、システムに既に保存されているServiceとDeviceのためのものです。デバイスとシステムに対して検証チェックを実行します。

# 引数

  * `device::Device`: デバイス
  * `service::Service`: サービス
  * `sys::System`: システム
