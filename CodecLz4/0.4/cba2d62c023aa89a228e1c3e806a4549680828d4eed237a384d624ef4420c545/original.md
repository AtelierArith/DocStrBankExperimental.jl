```
LZ4SafeDecompressor(; kwargs...)
```

Creates an LZ4 compression codec.

# Keywords

  * `block_size::Integer=1024`: The size in bytes of unecrypted data contained in each block.   Must match or exceed the compression `block_size` or decompression will fail.
