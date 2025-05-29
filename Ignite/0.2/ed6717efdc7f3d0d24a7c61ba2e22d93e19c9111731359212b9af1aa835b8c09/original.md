```julia
timeout_filter(timeout::Real) -> Ignite.TimeoutFilter
timeout_filter(
    timeout::Real,
    start_time::Real
) -> Ignite.TimeoutFilter

```

Creates an event filter function for use in a `FilteredEvent` that returns `true` if at least `timeout` seconds has passed since the filter function was created.
