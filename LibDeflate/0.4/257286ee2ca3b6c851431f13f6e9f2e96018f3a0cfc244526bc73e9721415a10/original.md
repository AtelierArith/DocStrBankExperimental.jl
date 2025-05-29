```
zlib_compress!(
    ::Compressor, output, input
)::Union{LibDeflateError, Int}
```

Zlib compress from `input` to `output`. Return the number of bytes written, or a `LibDeflateError`.

See also: [`unsafe_zlib_compress!`](@ref)
