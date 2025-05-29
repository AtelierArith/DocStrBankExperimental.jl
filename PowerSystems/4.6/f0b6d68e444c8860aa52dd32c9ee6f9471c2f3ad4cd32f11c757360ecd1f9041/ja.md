```
mutable struct ReactivePowerPI <: ReactivePowerControl
    Kp_q::Float64
    Ki_q::Float64
    ωf::Float64
    V_ref::Float64
    Q_ref::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
end
```

指定された電力リファレンスのための比例-積分リアクティブパワーコントローラのパラメータ

# 引数

  * `Kp_q::Float64`: 比例ゲイン、検証範囲: `(0, nothing)`
  * `Ki_q::Float64`: 積分ゲイン、検証範囲: `(0, nothing)`
  * `ωf::Float64`: フィルタ周波数カットオフ、検証範囲: `(0, nothing)`
  * `V_ref::Float64`: (デフォルト: `1.0`) 電圧セットポイント (pu)、検証範囲: `(0, nothing)`
  * `Q_ref::Float64`: (デフォルト: `1.0`) リアクティブパワーセットポイント (pu)、検証範囲: `(0, nothing)`
  * `ext::Dict{String, Any}`: (デフォルト: `Dict{String, Any}()`) シミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度。
  * `states::Vector{Symbol}`: (**変更しないでください。**) ReactivePowerPIモデルの[状態](@ref S)は次のとおりです:

```
σq_oc: PIコントローラの積分器状態、
q_oc: インバータモデルの測定されたリアクティブパワー
```

  * `n_states::Int`: (**変更しないでください。**) ReactivePowerPIは2つの状態を持ちます。
