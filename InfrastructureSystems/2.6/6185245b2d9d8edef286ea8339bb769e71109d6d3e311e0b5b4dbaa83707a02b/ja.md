```julia
has_time_series(
    owner::Union{InfrastructureSystems.InfrastructureSystemsComponent, InfrastructureSystems.SupplementalAttribute};
    kwargs...
) -> Bool

```

コンポーネントまたは補足属性が時系列データを持っている場合はtrueを返します。
