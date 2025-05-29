```
readPeriods(rpu::Union{RedPitaya,RedPitayaCluster, RedPitayaClusterView}, startPeriod, numPeriods, numBlockAverages=1, numPeriodsPerPatch=1; rpInfo=nothing, chunkSize = 50000, useCalibration = false)
```

Request and receive `numPeriods` Periods from `startPeriod` on.

See [`readSamples`](@ref), [`convertSamplesToPeriods!`](@ref), [`samplesPerPeriod`](@ref).

# Arguments

  * `rpu::Union{RedPitaya,RedPitayaCluster, RedPitayaClusterView}`: `RedPitaya`s to receive samples from.
  * `startPeriod`: period from which to start transmitting
  * `numPeriods`: number of periods to read
  * `numBlockAverages=1`: see `convertSamplesToPeriods`
  * `chunkSize=50000`: see `readSamples`
  * `rpInfo=nothing`: see `readSamples`
  * `useCalibration`: convert samples based on `RedPitaya`s calibration
