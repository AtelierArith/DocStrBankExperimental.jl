```
readFrames(rpu::Union{RedPitaya,RedPitayaCluster, RedPitayaClusterView}, startFrame, numFrames, numBlockAverages=1, numPeriodsPerPatch=1; rpInfo=nothing, chunkSize = 50000, useCalibration = false)
```

Request and receive `numFrames` frames from `startFrame` on.

See [`readSamples`](@ref), [`convertSamplesToFrames`](@ref), [`samplesPerPeriod`](@ref), [`periodsPerFrame`](@ref), [`updateCalib!`](@ref).

# Arguments

  * `rpu::Union{RedPitaya,RedPitayaCluster, RedPitayaClusterView}`: `RedPitaya`s to receive samples from.
  * `startFrame`: frame from which to start transmitting
  * `numFrames`: number of frames to read
  * `numBlockAverages=1`: see `convertSamplesToFrames`
  * `numPeriodsPerPatch=1`: see `convertSamplesToFrames`
  * `chunkSize=50000`: see `readSamples`
  * `rpInfo=nothing`: see `readSamples`
  * `useCalibration`: convert from Int16 samples to Float32 values based on `RedPitaya`s calibration
