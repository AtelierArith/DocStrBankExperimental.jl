```
struct CaptureProcessEmissions{T} <: CaptureData{T}

CaptureProcessEmissions(emissions::Dict{<:ResourceEmit, T}, co2_capture::Float64) where T
```

プロセスの排出量をキャプチャしますが、エネルギー使用に関連する排出量はキャプチャしません。

# フィールド

  * **`emissions::Dict{ResourceEmit, T}`** は、変数 `:cap_use` を通じての容量使用あたりのプロセス排出量です。
  * **`co2_capture::Float64`** は、CO₂キャプチャ率です。
