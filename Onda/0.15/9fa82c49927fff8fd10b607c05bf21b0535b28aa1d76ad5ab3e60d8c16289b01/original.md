```
AbstractLPCMFormat
```

A type whose subtypes represents byte/stream formats that can be (de)serialized to/from Onda's standard interleaved LPCM representation.

All subtypes of the form `F<:AbstractLPCMFormat` must call [`Onda.register_lpcm_format!`](@ref) and define an appropriate [`file_format_string`](@ref) method.

See also:

  * [`format`](@ref)
  * [`deserialize_lpcm`](@ref)
  * [`deserialize_lpcm_callback`](@ref)
  * [`serialize_lpcm`](@ref)
  * [`LPCMFormat`](@ref)
  * [`LPCMZstFormat`](@ref)
  * [`AbstractLPCMStream`](@ref)
