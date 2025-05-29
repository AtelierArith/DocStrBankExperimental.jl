```
@version SamplesInfoV2 begin
    sensor_type::String
    channels::Vector{String}
    sample_unit::String
    sample_resolution_in_unit::Float64
    sample_offset_in_unit::Float64
    sample_type::String = onda_sample_type_from_julia_type(sample_type)
    sample_rate::Float64
end
```

A Legolas-generated record type representing the bundle of `onda.signal` fields that are intrinsic to a signal's sample data, leaving out extrinsic file or recording information. This is useful when the latter information is irrelevant or does not yet exist (e.g. if sample data is being constructed/manipulated in-memory without yet having been serialized).

See https://github.com/beacon-biosignals/Legolas.jl for details regarding Legolas record types.
