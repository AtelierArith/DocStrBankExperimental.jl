```
@version PlanV3 begin
    # EDF.SignalHeader fields
    label::String
    transducer_type::String
    physical_dimension::String
    physical_minimum::Float32
    physical_maximum::Float32
    digital_minimum::Float32
    digital_maximum::Float32
    prefilter::String
    samples_per_record::Int32
    # EDF.FileHeader field
    seconds_per_record::Float64
    # Onda.SignalV3 fields (channels -> channel), may be missing
    recording::Union{UUID,Missing} = passmissing(UUID)
    sensor_type::Union{Missing,AbstractString}
    sensor_label::Union{Missing,AbstractString}
    channel::Union{Missing,AbstractString}
    sample_unit::Union{Missing,AbstractString}
    sample_resolution_in_unit::Union{Missing,Float64}
    sample_offset_in_unit::Union{Missing,Float64}
    sample_type::Union{Missing,AbstractString}
    sample_rate::Union{Missing,Float64}
    # errors, use `nothing` to indicate no error
    error::Union{Nothing,String}
end
```

A Legolas-generated record type describing a single EDF signal-to-Onda channel conversion.  The columns are the union of

  * fields from `EDF.SignalHeader` (all mandatory)
  * the `seconds_per_record` field from `EDF.FileHeader` (mandatory)
  * fields from `Onda.SignalV3` (optional, may be `missing` to indicate failed conversion), except for `file_path`
  * `error`, which is `nothing` for a conversion that is or is expected to be successful, and a `String` describing the source of the error (with backtrace) in the case of a caught error.
