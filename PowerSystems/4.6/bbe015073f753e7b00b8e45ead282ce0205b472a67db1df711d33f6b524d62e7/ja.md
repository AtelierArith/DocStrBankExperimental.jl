```julia
convert_component!(
    sys::PowerSystems.System,
    line::PowerSystems.MonitoredLine,
    linetype::Type{PowerSystems.Line};
    kwargs...
)

```

MonitoredLineコンポーネントをLineコンポーネントに変換し、システム内の元のコンポーネントを置き換えます。
