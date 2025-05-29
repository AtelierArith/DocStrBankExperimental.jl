```julia
add_component!(
    sys::PowerSystems.System,
    component::PowerSystems.Component;
    skip_validation,
    kwargs...
)

```

Add a component to the system.

A component cannot be added to more than one `System`. Throws ArgumentError if the component's name is already stored for its concrete type. Throws ArgumentError if any Component-specific rule is violated. Throws InvalidValue if any of the component's field values are outside of defined valid range.

# Examples

```julia
sys = System(100.0)

# Add a single component.
add_component!(sys, bus)

# Add many at once.
buses = [bus1, bus2, bus3]
generators = [gen1, gen2, gen3]
foreach(x -> add_component!(sys, x), Iterators.flatten((buses, generators)))
```

See also [`add_components!`](@ref).
