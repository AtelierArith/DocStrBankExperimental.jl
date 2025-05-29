```julia
add_service!(
    sys::PowerSystems.System,
    service::PowerSystems.ConstantReserveGroup;
    skip_validation,
    kwargs...
)

```

[`add_component!`](@ref)と似ていますが、ConstantReserveGroup用です。

# 引数

  * `sys::System`: システム
  * `service::ConstantReserveGroup`: 追加するサービス
