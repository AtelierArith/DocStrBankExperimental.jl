```julia
with_units_base(
    f::Function,
    sys::PowerSystems.System,
    units::Union{InfrastructureSystems.UnitSystemModule.UnitSystem, String}
) -> Any

```

A "context manager" that sets the [`System`](@ref)'s [units base](@ref per_unit) to the given value, executes the function, then sets the units base back.

# Examples

```julia
active_power_mw = with_units_base(sys, UnitSystem.NATURAL_UNITS) do
    get_active_power(gen)
end
# now active_power_mw is in natural units no matter what units base the system is in
```
