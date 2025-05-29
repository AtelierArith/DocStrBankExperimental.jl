```
mutable struct MagnitudeOutputCurrentLimiter <: OutputCurrentLimiter
    I_max::Float64
    ext::Dict{String, Any}
end
```

Magnitude（円形）電流制御リミッターのパラメータ。インバータ出力電流の大きさのみを調整します。

# 引数

  * `I_max::Float64`: 電流制御器の入力電流の最大制限値（puで、[`DEVICE_BASE`](@ref per_unit)）、検証範囲: `(0, nothing)`
  * `ext::Dict{String, Any}`: （デフォルト: `Dict{String, Any}()`）シミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度など。
