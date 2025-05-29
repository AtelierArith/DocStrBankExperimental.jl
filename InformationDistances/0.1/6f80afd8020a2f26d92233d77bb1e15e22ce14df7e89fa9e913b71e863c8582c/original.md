```
CodecCompressor{ <: TranscodingStreams.Codec} <: AbstractCompressor
```

A compressor that uses a `TranscodingStreams.Codec` for compressing.

---

```
CodecCompressor{C <: TranscodingStreams.Codec}(;kwargs...)
```

Create a `CodecCompressor` for the codec `C` with a additional keyword arguments passed to the constructor of that codec.

# Examples

```jldoctest
julia> using CodecXz: XzCompressor

julia> CodecCompressor{XzCompressor}(; level=6)
CodecCompressor{XzCompressor}(Base.Iterators.Pairs(:level => 6))
```
