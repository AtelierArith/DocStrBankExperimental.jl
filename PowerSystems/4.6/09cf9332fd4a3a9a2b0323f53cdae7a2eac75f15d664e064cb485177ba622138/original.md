```julia
set_dynamic_injector!(
    static_injector::PowerSystems.StaticInjection,
    dynamic_injector::Union{Nothing, PowerSystems.DynamicInjection}
)

```

Any StaticInjection struct that wants to support dynamic injectors must implement this method to set the value.

The method is only for internal uses.
