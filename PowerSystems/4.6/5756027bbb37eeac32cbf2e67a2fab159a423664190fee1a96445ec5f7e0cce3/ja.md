```julia
convert_component!(
    sys::PowerSystems.System,
    line::PowerSystems.Line,
    linetype::Type{PowerSystems.MonitoredLine};
    kwargs...
)

```

ラインコンポーネントをモニタードラインコンポーネントに変換し、システム内の元のものを置き換えます。
