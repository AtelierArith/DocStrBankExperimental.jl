```
DeflateCompressorStream(stream::IO; kwargs...)
```

Create a deflate compression stream (see `DeflateCompressor` for `kwargs`).

!!! warning
    `serialize` and `deepcopy` will not work with this stream due to stored raw pointers.

