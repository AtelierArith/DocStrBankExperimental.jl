```julia
set_contributing_services!(
    sys::PowerSystems.System,
    service::PowerSystems.ConstantReserveGroup,
    val::Vector{<:PowerSystems.Service}
)

```

ConstantReserveGroupのcontributing_servicesをチェック付きで設定します。
