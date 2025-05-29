```
DeflateDecompressorStream(stream::IO; kwargs...)
```

Create a deflate decompression stream (see `DeflateDecompressor` for `kwargs`).

!!! warning
    `serialize` and `deepcopy` will not work with this stream due to stored raw pointers.

