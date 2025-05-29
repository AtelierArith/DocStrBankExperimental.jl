```
readSamples(rpu::Union{RedPitaya,RedPitayaCluster, RedPitayaClusterView}, wpStart::Int64, numOfRequestedSamples::Int64, channel::Channel; chunkSize::Int64 = 25000)
```

`wpStart`から`numOfRequestedSamples`サンプルをパイプライン方式で要求し、受信します。サンプルと関連する`PerformanceData`は、`channel`に`SampleChunk`としてプッシュされます。

[`SampleChunk`](@ref)を参照してください。
