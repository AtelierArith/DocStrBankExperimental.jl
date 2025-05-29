```
pull_sample!(data::Vector{T}, inlet::StreamInfo; timeout = LSL_FOREVER)
```

Pull a sample from the inlet and assign to provided vector.

Function may throw timeout error, lost error if the stream has been lost. Note that if a timeout occurrs, or if a timeout of 0.0 is specified an no new sample is available, the  timestamp will be 0.0.

# Keyword arguments

`timeout::Number`: timeout to acquire the sample.
