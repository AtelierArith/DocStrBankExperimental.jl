```julia
sync_get_video_with_res(
    index::Integer,
    res::Freenect.Resolution,
    fmt::Freenect.VideoFormat
) -> Tuple{Union{Array{UInt8, 3}, Matrix{UInt8}}, Int64}

```

Synchronous video function, starts the runloop if it isn't running.

The returned array is copied before returning and is safe to store.
