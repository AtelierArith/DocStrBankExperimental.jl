```
compressed_lengths(compressor, iter)
```

`iter`内の各`s`について、`compressor`で圧縮したときの結果のバイト数を計算します。

`AbstractCompressor`の特定のサブタイプに対してこのメソッドを実装することで、いくつかの圧縮器は圧縮する前にリソースを割り当てる必要があるため、バッチ処理がパフォーマンスの向上につながる可能性があります。リソースは一度だけ割り当てられる必要があります。

カスタムサブタイプ`Compressor <: AbstractCompressor`に対してこのメソッドを実装することが推奨されますが、必須ではありません。その場合、メソッドシグネチャは`compressed_lengths(compressor::Compressor, iter)`であるべきです。

Juliaはイテレータのeltypeを指定することを許可していないため、`iter`の要素が`InformationDistances.ByteData`型であることを少なくとも確認し、オプションで`AbstractString`型であることも確認する必要があります。

# 例

```jldoctest
julia> compressed_lengths(LibDeflateCompressor(), ["hello", "world", "!"])
3-element Array{Int64,1}:
 10
 10
  6
```
