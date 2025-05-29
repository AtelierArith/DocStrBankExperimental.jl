```julia
filter_components_by_subsystem!(
    sys::PowerSystems.System,
    subsystem::AbstractString;
    runchecks
)

```

サブシステムに属さないすべてのコンポーネントを除外します。
