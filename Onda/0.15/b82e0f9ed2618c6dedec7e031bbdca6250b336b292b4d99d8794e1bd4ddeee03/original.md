```
deserializing_lpcm_stream(format::AbstractLPCMFormat, io)
```

Return a `stream::AbstractLPCMStream` that wraps `io` to enable direct LPCM deserialization from `io` via [`deserialize_lpcm`](@ref).

Note that `stream` must be finalized after usage via [`finalize_lpcm_stream`](@ref). Until `stream` is finalized, `io` should be considered to be part of the internal state of `stream` and should not be directly interacted with by other processes.
