```julia
sync_get_depth(
    index::Integer,
    fmt::Freenect.DepthFormat
) -> Tuple{Matrix{UInt16}, Int64}

```

Synchronous depth function with resolution `resolution_medium`, starts the runloop if it isn't running.

The returned array is copied before returning and is safe to store.
