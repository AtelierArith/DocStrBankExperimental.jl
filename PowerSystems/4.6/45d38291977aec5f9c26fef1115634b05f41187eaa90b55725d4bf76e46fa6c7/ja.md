```
mutable struct ActivePowerPI <: ActivePowerControl
    Kp_p::Float64
    Ki_p::Float64
    ωz::Float64
    P_ref::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
end
```

指定された電力リファレンスのための比例-積分アクティブパワーコントローラのパラメータ

# 引数

  * `Kp_p::Float64`: 比例ゲイン、検証範囲: `(0, nothing)`
  * `Ki_p::Float64`: 積分ゲイン、検証範囲: `(0, nothing)`
  * `ωz::Float64`: フィルタ周波数カットオフ、検証範囲: `(0, nothing)`
  * `P_ref::Float64`: (デフォルト: `1.0`) リファレンスパワーセットポイント (pu)、検証範囲: `(0, nothing)`
  * `ext::Dict{String, Any}`: (デフォルト: `Dict{String, Any}()`) シミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度。
  * `states::Vector{Symbol}`: (**変更しないでください。**) ActivePowerPIモデルの[状態](@ref S)は次のとおりです:

```
σp_oc: PIコントローラの積分器状態、
p_oc: インバータモデルの測定されたアクティブパワー
```

  * `n_states::Int`: (**変更しないでください。**) ActivePowerPIは2つの状態を持ちます
