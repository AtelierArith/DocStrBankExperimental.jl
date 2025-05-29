```julia
sync_get_tilt_state(state, index) -> Int32

```

Tilt state function, starts the runloop if it isn't running.

The returned pointer is only safe until the next call to this function.
