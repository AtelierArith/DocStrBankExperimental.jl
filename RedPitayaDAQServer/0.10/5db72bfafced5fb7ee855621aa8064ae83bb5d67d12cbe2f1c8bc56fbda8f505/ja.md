```
convertSamplesToFrames!(rpu::Union{RedPitayaCluster, RedPitayaClusterView}, samples, frames, numChan, numSampPerPeriod, numPeriods, numFrames, numTrueSampPerPeriod, numBlockAverages=1, numPeriodsPerPatch=1)
```

指定されたサンプルのセットをフレームにインプレースで変換します。

[`readFrames`](@ref)を参照してください。
