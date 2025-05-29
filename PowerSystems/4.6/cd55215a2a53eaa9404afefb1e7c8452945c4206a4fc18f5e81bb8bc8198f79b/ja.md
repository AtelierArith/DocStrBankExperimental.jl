```
mutable struct InstantaneousOutputCurrentLimiter <: OutputCurrentLimiter
    Id_max::Float64
    Iq_max::Float64
    ext::Dict{String, Any}
end
```

瞬時（平方）電流制御リミッタのパラメータ。インバータの出力電流をd軸とq軸で別々に調整します。

# 引数

  * `Id_max::Float64`: d軸電流制御器の入力電流の最大制限（puで、[`DEVICE_BASE`](@ref per_unit)）、検証範囲: `(0, nothing)`
  * `Iq_max::Float64`: q軸電流制御器の入力電流の最大制限（puで、[`DEVICE_BASE`](@ref per_unit)）、検証範囲: `(0, nothing)`
  * `ext::Dict{String, Any}`: (デフォルト: `Dict{String, Any}()`) シミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度など。
