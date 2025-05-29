```julia
add_component!(
    sys::PowerSystems.System,
    dyn_injector::PowerSystems.DynamicInjection,
    static_injector::PowerSystems.StaticInjection;
    kwargs...
)

```

Add a dynamic injector to the system.

A component cannot be added to more than one `System`. Throws ArgumentError if the name does not match the `static_injector` name. Throws ArgumentError if the `static_injector` is not attached to the system.

All rules for the generic `add_component!` method also apply.
