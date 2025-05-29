```
readSamples(rpu::Union{RedPitaya,RedPitayaCluster, RedPitayaClusterView}, wpStart::Int64, numOfRequestedSamples::Int64; chunkSize::Int64 = 25000, rpInfo=nothing)
```

`wpStart`から`numOfRequestedSamples`サンプルをパイプライン方式で要求し、受信します。サンプルの行列を返します。

`rpInfo`が`RPInfo`に設定されている場合、`chunkSize`サンプルごとに送信される`PerformanceData`は`rpInfo`にプッシュされます。
