```
NormalizedCompressionDistance{<: AbstractCompressor} <: Distances.PreMetric
```

2つの文字列間の`正規化圧縮距離`メトリック。

このメトリックは次のように定義されます：$d(x, y) := \frac{Z(xy) - \min(Z(x), Z(y))} {\max(Z(x), Z(y))}$

ここで、`Z(x)`は、特定の圧縮コーデックを使用して文字列`x`を圧縮したときの長さです。

---

```
NormalizedCompressionDistance(, [compressor::AbstractCompressor])
```

`NormalizedCompressionDistance`を作成します。

# 引数

  * `compressor` 使用する圧縮器。指定しない場合は、`CodecCompressor{CodecXz.XzCompressor}(;level=9; check=CodecXz.LZMA_CHECK_NONE)`が使用されます。

# 例

```jldoctest
julia> d1 = NormalizedCompressionDistance()
NormalizedCompressionDistance{CodecCompressor{CodecXz.XzCompressor}}(CodecCompressor{CodecXz.XzCompressor}(Base.Iterators.Pairs{Symbol,Signed,Tuple{Symbol,Symbol},NamedTuple{(:level, :check),Tuple{Int64,Int32}}}(:level => 9,:check => 0)))

julia> d1("hello", "world")
0.07142857142857142

julia> d2 = NormalizedCompressionDistance(LibDeflateCompressor())
NormalizedCompressionDistance{LibDeflateCompressor}(LibDeflateCompressor(12))

julia> d2("hello", "world")
0.5
```
