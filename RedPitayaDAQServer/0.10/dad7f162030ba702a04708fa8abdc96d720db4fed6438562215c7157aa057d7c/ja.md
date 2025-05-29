```
convertSamplesToPeriods!(rpu::Union{RedPitaya, RedPitayaCluster, RedPitayaClusterView}, samples, periods, numChan, numSampPerPeriod, numPeriods, numBlockAverages=1)
```

指定されたサンプルのセットをインプレースで期間に変換します。

[`readPeriods`](@ref)を参照してください。
