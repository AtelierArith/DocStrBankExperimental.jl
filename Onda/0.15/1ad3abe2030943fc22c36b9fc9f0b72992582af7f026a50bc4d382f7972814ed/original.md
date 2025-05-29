```
deserialize_lpcm(format::AbstractLPCMFormat, bytes,
                 samples_offset::Integer=0,
                 samples_count::Integer=typemax(Int))
deserialize_lpcm(stream::AbstractLPCMStream,
                 samples_offset::Integer=0,
                 samples_count::Integer=typemax(Int))
```

Return a channels-by-timesteps `AbstractMatrix` of interleaved LPCM-encoded sample data by deserializing the provided `bytes` in the given `format`, or from the given `stream` constructed by [`deserializing_lpcm_stream`](@ref).

Note that this operation may be performed in a zero-copy manner such that the returned sample matrix directly aliases `bytes`.

The returned segment is at most `sample_offset` samples offset from the start of `stream`/`bytes` and contains at most `sample_count` samples. This ensures that overrun behavior is generally similar to the behavior of `Base.skip(io, n)` and `Base.read(io, n)`.

This function is the inverse of the corresponding [`serialize_lpcm`](@ref) method, i.e.:

```
serialize_lpcm(format, deserialize_lpcm(format, bytes)) == bytes
```
