```julia
set_units_base_system!(
    system::PowerSystems.System,
    units::Union{InfrastructureSystems.UnitSystemModule.UnitSystem, String}
)

```

Sets the units base for the getter functions on the devices. It modifies the behavior of all getter functions

# Examples

```julia
set_units_base_system!(sys, "NATURAL_UNITS")
```

```julia
set_units_base_system!(sys, UnitSystem.SYSTEM_BASE)
```
