```
Bzip2DecompressorStream(stream::IO; kwargs...)
```

Create a bzip2 decompression stream (see `Bzip2Decompressor` for `kwargs`).

!!! warning
    `serialize` and `deepcopy` will not work with this stream due to stored raw pointers.

