```julia
System(
    base_power::Float64,
    buses::Vector{PowerSystems.ACBus},
    components...;
    kwargs...
) -> PowerSystems.System

```

コンポーネントが外部で構築されるときのSystemコンストラクタ。
