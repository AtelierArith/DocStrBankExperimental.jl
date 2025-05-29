```julia
get_available_component(
    sys::PowerSystems.System,
    uuid::Base.UUID
) -> Union{Nothing, InfrastructureSystems.InfrastructureSystemsComponent}

```

UUIDによって利用可能なコンポーネントを取得します。
