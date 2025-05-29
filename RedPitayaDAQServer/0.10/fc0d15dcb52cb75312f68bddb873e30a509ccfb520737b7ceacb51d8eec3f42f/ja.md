```
readFrames(rpu::Union{RedPitaya,RedPitayaCluster, RedPitayaClusterView}, startFrame, numFrames, numBlockAverages=1, numPeriodsPerPatch=1; rpInfo=nothing, chunkSize = 50000, useCalibration = false)
```

`startFrame` から `numFrames` フレームを要求して受信します。

[`readSamples`](@ref)、[`convertSamplesToFrames`](@ref)、[`samplesPerPeriod`](@ref)、[`periodsPerFrame`](@ref)、[`updateCalib!`](@ref) を参照してください。

# 引数

  * `rpu::Union{RedPitaya,RedPitayaCluster, RedPitayaClusterView}`: サンプルを受信する `RedPitaya`。
  * `startFrame`: 送信を開始するフレーム
  * `numFrames`: 読み取るフレームの数
  * `numBlockAverages=1`: `convertSamplesToFrames` を参照
  * `numPeriodsPerPatch=1`: `convertSamplesToFrames` を参照
  * `chunkSize=50000`: `readSamples` を参照
  * `rpInfo=nothing`: `readSamples` を参照
  * `useCalibration`: `RedPitaya` のキャリブレーションに基づいて Int16 サンプルを Float32 値に変換します
