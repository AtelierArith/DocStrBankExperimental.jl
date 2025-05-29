```
unsafe_gzip_decompress!(
    ::Decompressor, out_data::Vector{UInt8},
    max_outlen::Integer, in_ptr::Ptr, len::Integer,
    extra_data::Union{Vector{GzipExtraField}, Nothing}
)::Union{LibDeflateError, GzipDecompressResult}
```

Use the `Decompressor` to decompress gzip data at `in_ptr` and `len` bytes forward into `out_data`. If there is not enough room at `out_data`, resize `out_data`, except if it would be bigger than `max_outlen`, in that case return an error. If `extra_data` is not `nothing`, reuse the vector by overwriting.

Return a `GzipDecompressResult`

See also: [`gzip_decompress!`](@ref)
