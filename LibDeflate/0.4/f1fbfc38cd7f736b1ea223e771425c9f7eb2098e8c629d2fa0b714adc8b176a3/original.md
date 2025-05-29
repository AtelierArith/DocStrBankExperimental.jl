```
Compressor(compresslevel::Int=6)
```

Create an object which can compress using the DEFLATE algorithm. `compresslevel` can be from 1 (fast) to 12 (slow), and defaults to 6. The same compressor cannot be used by multiple threads at the same time. To parallelize compression, create multiple instances of `Compressor` and use one for each thread. Creating this object allocates, so when compressing multiple blocks, keep the same compressor in memory rather than making one for each block.

See also: [`compress!`](@ref), [`unsafe_compress!`](@ref)
