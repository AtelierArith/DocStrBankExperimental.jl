```
compressed_length(compressor, s)
```

The number of resulting bytes when `s` is compressed with `compressor`.

When implementing a subtype `Compressor <: AbstractCompressor` one should implement `compressed_length(compressor::Compressor, s::InformationDistances.ByteData)

# Examples

```jldoctest
julia> compressed_length(LibDeflateCompressor(), "hello")
10
```
