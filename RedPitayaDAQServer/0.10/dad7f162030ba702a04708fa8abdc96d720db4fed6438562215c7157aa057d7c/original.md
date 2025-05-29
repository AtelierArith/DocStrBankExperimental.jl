```
convertSamplesToPeriods!(rpu::Union{RedPitaya, RedPitayaCluster, RedPitayaClusterView}, samples, periods, numChan, numSampPerPeriod, numPeriods, numBlockAverages=1)
```

Converts a given set of samples to periods in-place.

See [`readPeriods`](@ref)
