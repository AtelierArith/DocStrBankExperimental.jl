```
compressed_lengths(compressor, iter)
```

Calculate for each `s` in `iter` the number of resulting bytes when `s` is compressed with `compressor`.

Implementing this method for a specific subtype of `AbstractCompressor` might lead to some performance improvements as some compressors need to allocate some resources before compressing, therefore batch processing might lead to performance improvements as the resources have to be allocated only once.

It is recommended but not necessary to implement this method for a custom subtype `Compressor <: AbstractCompressor`. The method signature in that case should be `compressed_lengths(compressor::Compressor, iter)`.

As Julia does not allow one to specify the eltype of an iterator, one should make at least sure, that the elements of `iter` can be of type `InformationDistances.ByteData` and optionally could also be of type `AbstractString`.

# Examples

```jldoctest
julia> compressed_lengths(LibDeflateCompressor(), ["hello", "world", "!"])
3-element Array{Int64,1}:
 10
 10
  6
```
