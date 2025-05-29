```
pull_sample(inlet::StreamInfo; timeout = LSL_FOREVER)
```

Pull a sample from the inlet and return as a vector of appropriate type.

Function may throw timeout error, lost error if the stream has been lost. Note that if a timeout occurrs, or if a timeout of 0.0 is specified an no new sample is available, the  timestamp will be 0.0.

# Keyword arguments

`timeout::Number`: timeout to acquire the sample.
