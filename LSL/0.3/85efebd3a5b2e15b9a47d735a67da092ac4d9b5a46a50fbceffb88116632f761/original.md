```
pull_chunk(inlet::StreamInfo; max_samples = 1024, timeout = LSL_FOREVER)
```

Pull a chunk of data from the inlet and assign to provided matrix.

Function returns a vector of timestamps of length N, being <= `max_samples` alongside a  matrix of data where each column consists of a sample such that size(data) = (M,N)

Function may throw timeout error, lost error if the stream has been lost. Note that if a timeout occurrs, or if a timeout of 0.0 is specified an no new sample is available, the  timestamp will be 0.0.

# Keyword arguments

`timeout::Number`: timeout to acquire the sample.
