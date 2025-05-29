```
unsafe_gzip_compress!(
    compressor::Compressor,
    out_ptr::Ptr, out_len::Integer,
    in_ptr::Ptr, in_len::Integer,
    comment::Union{Nothing, ReadableMemory},
    filename::Union{Nothing, ReadableMemory},
    extra::Union{Nothing, ReadableMemory},
    header_crc::Bool
)::Union{LibDeflateError, Int}
```

Use the `Compressor` to gzip compress input at `in_ptr` and `in_len` bytes onwards to, `out_ptr`. If the resulting gzip data could be longer than `out_len`, return an error. Optionally, include gzip comment, filename or extra data. All these must be `nothing` if not applicable.

Adds optional data `comment`, `filename`, `extra`. 

  * `comment` and `filename` must not include the byte `0x00`.
  * `extra` must be at most `typemax(UInt16)` bytes long.

Returns the number of bytes written to `out_ptr`.

See also: [`gzip_compress!`](@ref)
