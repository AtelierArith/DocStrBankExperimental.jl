```
readSamples(rpu::Union{RedPitaya,RedPitayaCluster, RedPitayaClusterView}, wpStart::Int64, numOfRequestedSamples::Int64; chunkSize::Int64 = 25000, rpInfo=nothing)
```

Request and receive `numOfRequestedSamples` samples from `wpStart` on in a pipelined fashion. Return a matrix of samples.

If `rpInfo` is set to a `RPInfo`, the `PerformanceData` sent after every `chunkSize` samples will be pushed into `rpInfo`.
