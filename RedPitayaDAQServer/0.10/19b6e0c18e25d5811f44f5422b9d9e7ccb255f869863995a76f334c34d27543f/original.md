```
SampleChunk
```

Struct containing a matrix of samples and associated `PerformanceData`

# Fields

  * `samples::Matrix{Int16}`: `n`x`m` matrix containing `m` samples for `n` channel
  * `performance::Vector{PerformanceData}`: `PerformanceData` object for each RedPitaya that transmitted samples
