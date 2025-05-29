```julia
add_components!(sys::PowerSystems.System, components)

```

Add many components to the system at once.

A component cannot be added to more than one `System`. Throws ArgumentError if the component's name is already stored for its concrete type. Throws ArgumentError if any Component-specific rule is violated. Throws InvalidValue if any of the component's field values are outside of defined valid range.

# Examples

```julia
sys = System(100.0)

buses = [bus1, bus2, bus3]
generators = [gen1, gen2, gen3]
add_components!(sys, Iterators.flatten((buses, generators))
```
