```
Bzip2CompressorStream(stream::IO; kwargs...)
```

Create a bzip2 compression stream (see `Bzip2Compressor` for `kwargs`).

!!! warning
    `serialize` and `deepcopy` will not work with this stream due to stored raw pointers.

