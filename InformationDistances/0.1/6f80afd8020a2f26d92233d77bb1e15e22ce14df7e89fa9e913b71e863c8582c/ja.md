```
CodecCompressor{ <: TranscodingStreams.Codec} <: AbstractCompressor
```

`TranscodingStreams.Codec`を使用して圧縮するコンプレッサーです。

---

```
CodecCompressor{C <: TranscodingStreams.Codec}(;kwargs...)
```

コーデック`C`のための`CodecCompressor`を作成し、そのコーデックのコンストラクタに渡される追加のキーワード引数を指定します。

# 例

```jldoctest
julia> using CodecXz: XzCompressor

julia> CodecCompressor{XzCompressor}(; level=6)
CodecCompressor{XzCompressor}(Base.Iterators.Pairs(:level => 6))
```
