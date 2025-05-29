```julia
sync_get_video(
    index::Integer,
    fmt::Freenect.VideoFormat
) -> Tuple{Union{Array{UInt8, 3}, Matrix{UInt8}}, Int64}

```

Synchronous video function with resolution `resolution_medium`, starts the runloop if it isn't running.

The returned array is copied before returning and is safe to store.
