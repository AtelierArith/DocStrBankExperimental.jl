```julia
throttle_filter(throttle::Real) -> Ignite.ThrottleFilter
throttle_filter(
    throttle::Real,
    last_fire::Real
) -> Ignite.ThrottleFilter

```

Creates an event filter function for use in a `FilteredEvent` that returns `true` if at least `throttle` seconds has passed since it was last fired.
