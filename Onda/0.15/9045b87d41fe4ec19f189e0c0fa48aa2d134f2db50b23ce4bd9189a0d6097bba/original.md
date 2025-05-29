```
serialize_lpcm(format::AbstractLPCMFormat, samples::AbstractMatrix)
serialize_lpcm(stream::AbstractLPCMStream, samples::AbstractMatrix)
```

Return the `AbstractVector{UInt8}` of bytes that results from serializing `samples` to the given `format` (or serialize those bytes directly to `stream`) where `samples` is a channels-by-timesteps matrix of interleaved LPCM-encoded sample data.

Note that this operation may be performed in a zero-copy manner such that the returned `AbstractVector{UInt8}` directly aliases `samples`.

This function is the inverse of the corresponding [`deserialize_lpcm`](@ref) method, i.e.:

```
deserialize_lpcm(format, serialize_lpcm(format, samples)) == samples
```
