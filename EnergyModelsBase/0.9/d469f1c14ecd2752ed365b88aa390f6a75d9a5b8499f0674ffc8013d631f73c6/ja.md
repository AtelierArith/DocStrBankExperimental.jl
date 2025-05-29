```
struct CaptureProcessEnergyEmissions{T} <: CaptureData{T}

CaptureProcessEnergyEmissions(emissions::Dict{<:ResourceEmit, T}, co2_capture::Float64) where T
```

プロセス排出量とエネルギー使用に関連する排出量の両方をキャプチャします。

# フィールド

  * **`emissions::Dict{ResourceEmit, T}`** は、変数 `:cap_use` を通じての容量使用あたりのプロセス排出量です。
  * **`co2_capture::Float64`** は、CO₂キャプチャ率です。
