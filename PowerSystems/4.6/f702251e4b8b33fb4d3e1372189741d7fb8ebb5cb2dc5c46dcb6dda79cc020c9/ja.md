```julia
add_service!(
    sys::PowerSystems.System,
    service::PowerSystems.Service,
    contributing_devices;
    kwargs...
)

```

[`add_component!`](@ref)と似ていますが、サービス用です。

# 引数

  * `sys::System`: システム
  * `service::Service`: 追加するサービス
  * `contributing_devices`: デバイスタイプの反復可能なオブジェクトでなければなりません。
