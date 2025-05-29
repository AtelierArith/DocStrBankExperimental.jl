```julia
convert_component!(
    sys::PowerSystems.System,
    line::PowerSystems.Line,
    linetype::Type{PowerSystems.MonitoredLine};
    kwargs...
)

```

Converts a Line component to a MonitoredLine component and replaces the original in the system
