```
mutable struct PIDGOV <: TurbineGov
    feedback_flag::Int
    Rperm::Float64
    T_reg::Float64
    Kp::Float64
    Ki::Float64
    Kd::Float64
    Ta::Float64
    Tb::Float64
    D_turb::Float64
    gate_openings::Tuple{Float64, Float64, Float64}
    power_gate_openings::Tuple{Float64, Float64, Float64}
    G_lim::MinMax
    A_tw::Float64
    Tw::Float64
    V_lim::MinMax
    P_ref::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
    states_types::Vector{StateTypes}
    internal::InfrastructureSystemsInternal
end
```

PID制御器を持つ水力タービン-ガバナー。

# 引数

  * `feedback_flag::Int`: ガバナーのドロップ用フィードバック信号：電力の場合は0、ゲート位置の場合は1、検証範囲：`(0, 1)`
  * `Rperm::Float64`: スピードの永久ドロップパラメータ、検証範囲：`(0, nothing)`
  * `T_reg::Float64`: スピード検出器の時間定数、検証範囲：`(0, nothing)`
  * `Kp::Float64`: ガバナーの比例ゲイン、検証範囲：`(0, nothing)`
  * `Ki::Float64`: ガバナーの積分ゲイン、検証範囲：`(0, nothing)`
  * `Kd::Float64`: ガバナーの微分ゲイン、検証範囲：`(0, nothing)`
  * `Ta::Float64`: ガバナーの微分時間定数、検証範囲：`(0, nothing)`
  * `Tb::Float64`: ゲートサーボの時間定数、検証範囲：`(0, nothing)`
  * `D_turb::Float64`: タービンの減衰係数、検証範囲：`(0, nothing)`
  * `gate_openings::Tuple{Float64, Float64, Float64}`: 異なる負荷でのゲート開放速度
  * `power_gate_openings::Tuple{Float64, Float64, Float64}`: ゲート開放時の電力
  * `G_lim::MinMax`: 最小/最大ゲート開放 `(G_min, G_max)`。
  * `A_tw::Float64`: Twを乗算する係数、検証範囲：`(eps(), nothing)`
  * `Tw::Float64`: 水の慣性時間定数、秒、検証範囲：`(eps(), nothing)`
  * `V_lim::MinMax`: ゲート開放速度の制限 `(G_min, G_max)`。
  * `P_ref::Float64`: (デフォルト: `1.0`) 参照電力セットポイント (pu)、検証範囲：`(0, nothing)`
  * `ext::Dict{String, Any}`: (デフォルト: `Dict{String, Any}()`) シミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度。
  * `states::Vector{Symbol}`: (**変更しないでください。**) PIDGOVモデルの[状態](@ref S)は：

```
x_g1: フィルタされた入力測定値、
x_g2: PIブロック内部状態、
x_g3: 最初のレギュレータ状態、 
x_g4: 微分ブロック内部状態、 
x_g5: 2番目のレギュレータ状態、 
x_g6: ゲート位置状態、 
x_g7: 水の慣性状態
```

  * `n_states::Int`: (**変更しないでください。**) PIDGOVは7つの状態を持っています
  * `states_types::Vector{StateTypes}`: (**変更しないでください。**) PIDGOVは7つの[differential](@ref states_list) [状態](@ref S)を持っています
  * `internal::InfrastructureSystemsInternal`: (**変更しないでください。**) PowerSystems.jl内部参照
