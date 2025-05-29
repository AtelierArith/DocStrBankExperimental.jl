```
ZlibCompressorStream(stream::IO)
```

Create a zlib compression stream (see `ZlibCompressor` for `kwargs`).

!!! warning
    `serialize` and `deepcopy` will not work with this stream due to stored raw pointers.

