```
startPipelinedData(rpu::Union{RedPitayaCluster, RedPitayaClusterView}, reqWP::Int64, numSamples::Int64, chunkSize::Int64)
```

すべての `RedPitaya` に、書き込みポインタ `reqWP` から `numSamples` サンプルを `chunkSize` のチャンクで送信するよう指示します。

[`readSamples`](@ref) を参照してください。
