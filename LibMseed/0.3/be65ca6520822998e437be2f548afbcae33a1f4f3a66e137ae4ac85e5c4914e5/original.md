```
MseedTraceSegment{T}
```

Segment of continuous data of element type `T`.

# Fields

  * `starttime::NanosecondDateTime`: Date and time of first sample.
  * `endtime::NanosecondDateTime`: Date and time of last sample.
  * `sample_rate::Float64`: Nominal sampling rate in samples per second.
  * `sample_count::Int64`: Number of samples in trace coverage.
  * `data::Vector{T}`: Data values of trace.
