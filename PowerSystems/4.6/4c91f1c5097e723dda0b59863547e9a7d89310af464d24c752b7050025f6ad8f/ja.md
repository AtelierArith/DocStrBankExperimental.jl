```julia
add_service!(
    sys::PowerSystems.System,
    service::PowerSystems.Service,
    contributing_device::PowerSystems.Device;
    kwargs...
)

```

[`add_component!`](@ref)と似ていますが、サービス用です。

# 引数

  * `sys::System`: システム
  * `service::Service`: 追加するサービス
  * `contributing_device::Device`: 有効なデバイス
