```
gzip_decompress!(
    ::Decompressor, out::Vector{UInt8}, in_data, max_len=typemax(Int)
)::Union{GzipDecompressResult, LibDeflateError}
```

Gzip decompress the input data into `out`, and resize `out` to fit.

See also: [`unsafe_gzip_decompress!`](@ref)
