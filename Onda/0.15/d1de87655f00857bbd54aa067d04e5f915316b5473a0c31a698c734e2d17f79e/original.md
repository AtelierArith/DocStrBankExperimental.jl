```
deserialize_lpcm_callback(format::AbstractLPCMFormat, samples_offset, samples_count)
```

Return `(callback, required_byte_offset, required_byte_count)` where `callback` accepts the byte block specified by `required_byte_offset` and `required_byte_count` and returns the samples specified by `samples_offset` and `samples_count`.

As a fallback, this function returns `(callback, missing, missing)`, where `callback` requires all available bytes. `AbstractLPCMFormat` subtypes that support partial/block-based deserialization (e.g. the basic `LPCMFormat`) can overload this function to only request exactly the byte range that is required for the sample range requested by the caller.

This allows callers to handle the byte block retrieval themselves while keeping Onda's LPCM Serialization API agnostic to the caller's storage layer of choice.
