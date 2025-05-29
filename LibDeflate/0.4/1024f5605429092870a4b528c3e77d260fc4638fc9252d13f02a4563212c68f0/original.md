```
unsafe_zlib_compress!(
    ::Compressor,
    out_ptr::Ptr, max_outlen::Integer,
    in_ptr::Ptr, len::Integer
)::Union{LibDeflateError, Int}
```

Zlib compress data beginning at `in_ptr` and `len` bytes onwards, into `out_ptr`. Return the number of bytes written, or a `LibDeflateError`.

See also: [`zlib_compress!`](@ref)
