```
EmissionsData{T<:Union{TimeProfile,Float64}} <: Data
```

`EmissionsData`の抽象型は、異なるタイプのキャプチャ構成に基づいてディスパッチするために使用できます。

一般的に、異なるタイプは以下の入力を必要とします：

  * **`emissions::Dict{ResourceEmit, T}`** は、変数 `:cap_use` を通じての容量使用あたりのプロセス排出量です。`TimeProfile` または `Float64` としての入力を許可します。
  * **`co2_capture::Float64`** は、CO₂キャプチャ率です。

# タイプ

  * **[`CaptureProcessEnergyEmissions`](@ref)**: プロセス排出量とエネルギー使用に関連する排出量の両方をキャプチャします。
  * **[`CaptureProcessEmissions`](@ref)**: プロセス排出量をキャプチャしますが、エネルギー使用に関連する排出量はキャプチャしません。
  * **[`CaptureEnergyEmissions`](@ref)**: エネルギー使用に関連する排出量をキャプチャしますが、プロセス排出量はキャプチャしません。入力として `emissions` は必要ありません。
  * **[`EmissionsProcess`](@ref)**: キャプチャはありませんが、プロセス排出量は存在します。入力として `co2_capture` は必要ありませんが、提供された場合は無視されます。
  * **[`EmissionsEnergy`](@ref)**: キャプチャもプロセス排出量もありません。入力として `co2_capture` や `emissions` は必要ありませんが、提供された場合は無視されます。
