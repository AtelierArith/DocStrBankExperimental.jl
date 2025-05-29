```
gzip_decompress!(
    ::Decompressor, out::Vector{UInt8}, in_data, max_len=typemax(Int)
)::Union{GzipDecompressResult, LibDeflateError}
```

入力データを `out` に解凍し、`out` のサイズを調整します。

参照: [`unsafe_gzip_decompress!`](@ref)
