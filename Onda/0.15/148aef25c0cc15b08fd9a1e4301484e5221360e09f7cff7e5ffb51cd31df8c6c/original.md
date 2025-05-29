```
store(file_path, file_format::Union{AbstractString,AbstractLPCMFormat},
      samples::Samples, recording::UUID, start::Period,
      sensor_label::AbstractString = samples.info.sensor_type)
```

Serialize the given `samples` to `file_format` and write the output to `file_path`, returning a `SignalV2` instance constructed from the provided arguments.
