```
readPeriods(rpu::Union{RedPitaya,RedPitayaCluster, RedPitayaClusterView}, startPeriod, numPeriods, numBlockAverages=1, numPeriodsPerPatch=1; rpInfo=nothing, chunkSize = 50000, useCalibration = false)
```

`startPeriod`から`numPeriods`期間を要求し、受信します。

[`readSamples`](@ref)、[`convertSamplesToPeriods!`](@ref)、[`samplesPerPeriod`](@ref)を参照してください。

# 引数

  * `rpu::Union{RedPitaya,RedPitayaCluster, RedPitayaClusterView}`: サンプルを受信する`RedPitaya`。
  * `startPeriod`: 送信を開始する期間
  * `numPeriods`: 読み取る期間の数
  * `numBlockAverages=1`: `convertSamplesToPeriods`を参照
  * `chunkSize=50000`: `readSamples`を参照
  * `rpInfo=nothing`: `readSamples`を参照
  * `useCalibration`: `RedPitaya`のキャリブレーションに基づいてサンプルを変換する
