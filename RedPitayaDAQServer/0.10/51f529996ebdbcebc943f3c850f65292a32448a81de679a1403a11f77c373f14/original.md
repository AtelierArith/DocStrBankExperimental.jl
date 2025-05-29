```
readSamples(rpu::Union{RedPitaya,RedPitayaCluster, RedPitayaClusterView}, wpStart::Int64, numOfRequestedSamples::Int64, channel::Channel; chunkSize::Int64 = 25000)
```

Request and receive `numOfRequestedSamples` samples from `wpStart` on in a pipelined fashion. The samples and associated `PerformanceData` are pushed into `channel` as a `SampleChunk`.

See [`SampleChunk`](@ref).
