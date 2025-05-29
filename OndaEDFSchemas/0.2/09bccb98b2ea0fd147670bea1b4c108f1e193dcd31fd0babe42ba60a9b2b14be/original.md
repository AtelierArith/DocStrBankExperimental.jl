```
@version FilePlanV4 > PlanV4 begin
    recording::Union{UUID,Missing} = lift(UUID, recording)
    edf_signal_index::Int
    sensor_label::Union{String,Missing}
end
```

A Legolas-generated record type representing one EDF signal-to-Onda channel conversion, which includes the columns of a [`PlanV4`](@ref) and additional file-level context:

  * `recording::Union{UUID,Missing}` the UUID of the recording, if known.
  * `edf_signal_index` gives the index of the `signals` in the source `EDF.File` corresponding to this row
  * `sensor_label::AbstractString` gives the unique identifier of the corresponding output `Onda.Samples` after conversion.
