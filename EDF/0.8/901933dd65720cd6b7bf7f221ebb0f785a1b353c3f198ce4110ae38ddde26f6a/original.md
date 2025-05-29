```
EDF.FileHeader
```

Type representing the parsed header record of an `EDF.File` (excluding signal headers).

# Fields

  * `version::String`: data format version
  * `patient::Union{String,PatientID}`: local patient identification
  * `recording::Union{String,RecordingID}`: local recording identification
  * `start::DateTime`: start date/time of the recording
  * `is_contiguous::Bool`: if `true`, data records are contiguous; is `true` for non-EDF+-compliant files
  * `record_count::Int`: number of data records in the recording
  * `seconds_per_record::Float64`: duration of a data record in seconds
