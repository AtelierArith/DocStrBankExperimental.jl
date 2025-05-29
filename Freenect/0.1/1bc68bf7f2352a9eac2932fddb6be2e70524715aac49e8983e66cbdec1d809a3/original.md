```julia
sync_get_depth_with_res(
    index::Integer,
    res::Freenect.Resolution,
    fmt::Freenect.DepthFormat
) -> Tuple{Matrix{UInt16}, Int64}

```

Synchronous depth function, starts the runloop if it isn't running.

The returned array is copied before returning and is safe to store.
