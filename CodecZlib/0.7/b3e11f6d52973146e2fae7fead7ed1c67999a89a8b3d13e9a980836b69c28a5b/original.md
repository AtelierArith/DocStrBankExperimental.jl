```
GzipDecompressorStream(stream::IO; kwargs...)
```

Create a gzip decompression stream (see `GzipDecompressor` for `kwargs`).

!!! warning
    `serialize` and `deepcopy` will not work with this stream due to stored raw pointers.

