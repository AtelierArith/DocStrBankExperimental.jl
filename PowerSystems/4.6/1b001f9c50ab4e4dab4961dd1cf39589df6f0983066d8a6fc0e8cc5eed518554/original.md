```julia
get_max_reactive_power(
    d::PowerSystems.RenewableDispatch
) -> Any

```

Return the max reactive power for the Renewable Generation calculated as the rating * power*factor if reactive*power_limits is nothing
