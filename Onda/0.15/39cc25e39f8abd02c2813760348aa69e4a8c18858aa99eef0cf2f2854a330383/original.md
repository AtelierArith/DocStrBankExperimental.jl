```
LPCMFormat(channel_count::Int, sample_type::Type)
LPCMFormat(info::SamplesInfoV2)
```

Return a `LPCMFormat<:AbstractLPCMFormat` instance corresponding to Onda's default interleaved LPCM format assumed for sample data files with the "lpcm" extension.

`channel_count` corresponds to `length(info.channels)`, while `sample_type` corresponds to `sample_type(info)`

Note that bytes (de)serialized to/from this format are little-endian (per the Onda specification).
