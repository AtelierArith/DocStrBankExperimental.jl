```julia
get_max_reactive_power(d::PowerSystems.RenewableGen) -> Any

```

Return the max reactive power for the Renewable Generation calculated as the `rating` * sin(acos(`power_factor`))
