```julia
show_components(
    sys::PowerSystems.System,
    component_type::Type{<:PowerSystems.Component};
    ...
)
show_components(
    sys::PowerSystems.System,
    component_type::Type{<:PowerSystems.Component},
    additional_columns::Union{Dict, Vector};
    kwargs...
)

```

Show all components of the given type in a table.

# Arguments

  * `sys::System`: System containing the components.
  * `component_type::Type{<:Component}`: Type to display. Must be a concrete type.
  * `additional_columns::Union{Dict, Vector}`: Additional columns to display. The Dict option is a mapping of column name to function. The function must accept a component. The Vector option is an array of field names for the `component_type`.

Extra keyword arguments are forwarded to PrettyTables.pretty_table.

# Examples

```julia
show_components(sys, ThermalStandard)
show_components(sys, ThermalStandard, Dict("has_time_series" => x -> has_time_series(x)))
show_components(sys, ThermalStandard, [:active_power, :reactive_power])
```
