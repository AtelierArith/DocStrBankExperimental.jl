```
Stream{fmt}(io, filename=nothing)
```

Indicates that the stream `io` is written in known format [`DataFormat`](@ref) `fmt`. For example, `Stream{format"PNG"}(io)` would indicate PNG format. If known, the optional `filename` argument can be used to improve error messages, etc.

!!! compat
    `Stream{fmt}(io, ...)` requires FileIO 1.6 or higher. The deprecated syntax `Stream(fmt, io, ...)` works on all FileIO 1.x releases.

