```
gzip_compress!(
    compressor::Compressor,
    output::Vector{UInt8},
    input::ReadableMemory
    comment=nothing,
    filename=nothing,
    extra=nothing,
    header_crc::Bool=false
)::Union{LibDeflateError, Vector{UInt8}}
```

Gzip compress `input` into `output` and resizing output to fit. Returns `output`.

Adds optional data `comment`, `filename`, `extra`. All these must be `nothing` if not applicable.

  * `comment` and `filename` must not include the byte `0x00`.
  * `extra` must be at most `typemax(UInt16)` bytes long.

If `header_crc` is true, add the header CRC checksum.

See also: [`unsafe_gzip_compress!`](@ref)
