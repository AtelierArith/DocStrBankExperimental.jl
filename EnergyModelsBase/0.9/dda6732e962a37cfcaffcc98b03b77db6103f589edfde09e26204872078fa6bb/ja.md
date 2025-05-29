```
struct CaptureEnergyEmissions{T} <: CaptureData{T}

CaptureEnergyEmissions(emissions::Dict{<:ResourceEmit, T}, co2_capture::Float64) where T
CaptureEnergyEmissions(co2_capture::Float64)
```

エネルギー使用に関連する排出量をキャプチャしますが、プロセス排出量は含まれません。`emissions`を入力として必要としませんが、提供することはできます。

# フィールド

  * **`emissions::Dict{ResourceEmit, T}`** は、変数 `:cap_use` を通じた容量使用あたりのプロセス排出量です。
  * **`co2_capture::Float64`** は、CO₂キャプチャ率です。
