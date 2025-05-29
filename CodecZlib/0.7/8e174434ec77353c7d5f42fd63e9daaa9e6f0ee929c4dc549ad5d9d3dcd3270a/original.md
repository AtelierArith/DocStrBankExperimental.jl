```
GzipCompressorStream(stream::IO; kwargs...)
```

Create a gzip compression stream (see `GzipCompressor` for `kwargs`).

!!! warning
    `serialize` and `deepcopy` will not work with this stream due to stored raw pointers.

