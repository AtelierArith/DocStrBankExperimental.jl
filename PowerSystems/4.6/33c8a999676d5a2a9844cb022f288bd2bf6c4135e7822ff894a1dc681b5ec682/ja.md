```
mutable struct PriorityOutputCurrentLimiter <: OutputCurrentLimiter
    I_max::Float64
    ϕ_I::Float64
    ext::Dict{String, Any}
end
```

優先度ベースの電流制御リミッタのパラメータ。インバータ出力電流の大きさを調整し、結果として得られる電流信号の特定の角度を優先します。

# 引数

  * `I_max::Float64`: puでの電流制御器入力電流の最大制限 ([`DEVICE_BASE`](@ref per_unit))、検証範囲: `(0, nothing)`
  * `ϕ_I::Float64`: 制限I*maxに達したときのI*refのためのd軸に対して測定された事前定義された角度、検証範囲: `(-1.571, 1.571)`
  * `ext::Dict{String, Any}`: (デフォルト: `Dict{String, Any}()`) シミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度。
