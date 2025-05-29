```julia
add_service!(
    sys::PowerSystems.System,
    service::PowerSystems.ConstantReserveGroup,
    contributing_services::Vector{<:PowerSystems.Service};
    skip_validation,
    kwargs...
)

```

[`add_component!`](@ref)と似ていますが、ConstantReserveGroup用です。

# 引数

  * `sys::System`: システム
  * `service::ConstantReserveGroup`: 追加するサービス
  * `contributing_services`: グループに貢献するサービス
