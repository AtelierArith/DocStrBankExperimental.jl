```
zlib_decompress!(
    ::Decompressor, output, input, [n_out::Integer]
)::Union{LibDeflateError, Int}
```

Zlib decompress from `input` to `output`. If the precise number of decompressed bytes is known, pass it in as `n_out` for added performance. If it is wrong, the function will return an error.

Return the number of bytes written, or a `LibDeflateError`.

See also: [`unsafe_zlib_decompress!`](@ref)
