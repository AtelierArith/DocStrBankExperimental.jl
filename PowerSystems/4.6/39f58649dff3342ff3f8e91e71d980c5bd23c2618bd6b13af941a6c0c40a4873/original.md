```julia
copy_subcomponent_time_series!(
    subsystem::PowerSystems.StaticInjectionSubsystem,
    subcomponent::PowerSystems.Component
)

```

Efficiently add all time series data in the subcomponent to the subsystem by copying the underlying references.
