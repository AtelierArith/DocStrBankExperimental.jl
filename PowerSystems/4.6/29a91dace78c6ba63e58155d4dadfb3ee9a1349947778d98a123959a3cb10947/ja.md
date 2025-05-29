```julia
get_subsystem_components(
    sys::PowerSystems.System,
    subsystem_name::AbstractString
) -> Base.Generator{Set{Base.UUID}, InfrastructureSystems.var"#450#451"{InfrastructureSystems.SystemData}}

```

サブシステム内のすべてのコンポーネントのジェネレーターを返します。

サブシステム名が保存されていない場合はArgumentErrorをスローします。
