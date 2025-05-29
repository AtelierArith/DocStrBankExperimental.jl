```julia
sync_get_depth_with_res(
    depth,
    timestamp,
    index,
    res,
    fmt
) -> Int32

```

Synchronous depth function, starts the runloop if it isn't running

In the raw pointer version, the returned buffer is valid until this function is called again, after which the buffer must not be used again. Make a copy if the data is required. The version returning an array does not have this limitation.
