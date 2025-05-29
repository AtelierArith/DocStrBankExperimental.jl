```julia
get_time_series_resolutions(
    sys::PowerSystems.System;
    time_series_type
) -> Any

```

Return a sorted Vector of distinct resolutions for all time series of the given type (or all types).
