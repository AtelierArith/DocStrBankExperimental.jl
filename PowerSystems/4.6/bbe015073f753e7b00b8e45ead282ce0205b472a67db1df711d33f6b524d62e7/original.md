```julia
convert_component!(
    sys::PowerSystems.System,
    line::PowerSystems.MonitoredLine,
    linetype::Type{PowerSystems.Line};
    kwargs...
)

```

Converts a MonitoredLine component to a Line component and replaces the original in the system.
