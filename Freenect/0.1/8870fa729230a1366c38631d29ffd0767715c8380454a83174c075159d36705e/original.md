```julia
sync_get_video_with_res(
    video,
    timestamp,
    index,
    res,
    fmt
) -> Int32

```

Synchronous video function, starts the runloop if it isn't running

The returned buffer is valid until this function is called again, after which the buffer must not be used again. Make a copy if the data is required.
