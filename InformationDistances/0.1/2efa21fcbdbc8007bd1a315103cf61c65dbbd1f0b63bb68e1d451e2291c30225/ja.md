```
compressed_length(compressor, s)
```

`compressor`を使用して`s`を圧縮したときの結果のバイト数。

`Compressor <: AbstractCompressor`のサブタイプを実装する際は、`compressed_length(compressor::Compressor, s::InformationDistances.ByteData)`を実装する必要があります。

# 例

```jldoctest
julia> compressed_length(LibDeflateCompressor(), "hello")
10
```
