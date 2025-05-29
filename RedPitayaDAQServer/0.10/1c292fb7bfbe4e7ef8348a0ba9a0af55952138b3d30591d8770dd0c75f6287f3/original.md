```
startPipelinedData(rpu::Union{RedPitayaCluster, RedPitayaClusterView}, reqWP::Int64, numSamples::Int64, chunkSize::Int64)
```

Instruct all `RedPitaya`s to send `numSamples` samples from writepointer `reqWP` in chunks of `chunkSize`.

See [`readSamples`](@ref)
