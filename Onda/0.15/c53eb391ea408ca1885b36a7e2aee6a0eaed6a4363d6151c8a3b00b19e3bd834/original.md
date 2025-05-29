```
@version SignalV2 > SamplesInfoV2 begin
    recording::UUID
    file_path::(<:Any)
    file_format::String
    span::TimeSpan
    sensor_label::String
    sensor_type::String
    channels::Vector{String}
    sample_unit::String
end
```

A Legolas-generated record type representing an [`onda.signal` as described by the Onda Format Specification](https://github.com/beacon-biosignals/Onda.jl##ondasignal2).

Note that some fields documented as required fields of `onda.signal@2` in the Onda Format Specification are captured via this schema version's extension of `SamplesInfoV2`.

See https://github.com/beacon-biosignals/Legolas.jl for details regarding Legolas record types.
