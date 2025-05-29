```julia
sync_get_tilt_state(index::Integer) -> Freenect.RawTiltState

```

Tilt state function, starts the runloop if it isn't running.

The returned `RawTiltState` struct is safe to store.
