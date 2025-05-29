```
Decompressor()
```

Create an object which can decompress using the DEFLATE algorithm. The same decompressor cannot be used by multiple threads at the same time. To parallelize decompression, create multiple instances of `Decompressor` and use one for each thread. Creating this object allocates, so when decompressing multiple blocks, keep the same decompressor in memory rather than making one for each block.

See also: [`decompress!`](@ref), [`unsafe_decompress!`](@ref)
