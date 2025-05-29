```
ZlibDecompressorStream(stream::IO; kwargs...)
```

Create a deflate decompression stream (see `ZlibDecompressor` for `kwargs`).

!!! warning
    `serialize` and `deepcopy` will not work with this stream due to stored raw pointers.

