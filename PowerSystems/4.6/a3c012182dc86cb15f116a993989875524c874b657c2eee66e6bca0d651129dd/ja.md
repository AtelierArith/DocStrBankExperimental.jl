```
mutable struct WPIDHY <: TurbineGov
    T_reg::Float64
    reg::Float64
    Kp::Float64
    Ki::Float64
    Kd::Float64
    Ta::Float64
    Tb::Float64
    V_lim::MinMax
    G_lim::MinMax
    Tw::Float64
    P_lim::MinMax
    D::Float64
    gate_openings::Tuple{Float64, Float64, Float64}
    power_gate_openings::Tuple{Float64, Float64, Float64}
    P_ref::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
    states_types::Vector{StateTypes}
    internal::InfrastructureSystemsInternal
end
```

ウッドワードPID水力ガバナー

# 引数

  * `T_reg::Float64`: ガバナーの入力時間定数（秒）、検証範囲: `(0, nothing)`
  * `reg::Float64`: ガバナーゲインの入力、検証範囲: `(0, nothing)`
  * `Kp::Float64`: ガバナー比例ゲイン、検証範囲: `(0, nothing)`
  * `Ki::Float64`: ガバナー積分ゲイン、検証範囲: `(0, nothing)`
  * `Kd::Float64`: ガバナー微分ゲイン、検証範囲: `(0, nothing)`
  * `Ta::Float64`: ガバナー微分/高周波時間定数、検証範囲: `(0, nothing)`
  * `Tb::Float64`: ゲートサーボ時間定数、検証範囲: `(0, nothing)`
  * `V_lim::MinMax`: ゲート開放速度の制限 `(G_min, G_max)`。
  * `G_lim::MinMax`: 最小/最大ゲート速度 `(G_min, G_max)`。
  * `Tw::Float64`: 水の慣性時間定数、秒、検証範囲: `(eps(), nothing)`
  * `P_lim::MinMax`: 最小/最大ゲート開放 `(P_min, P_max)`。
  * `D::Float64`: タービンダンピング係数、検証範囲: `(0, nothing)`
  * `gate_openings::Tuple{Float64, Float64, Float64}`: 異なる負荷でのゲート開放速度
  * `power_gate_openings::Tuple{Float64, Float64, Float64}`: ゲート開放時の電力
  * `P_ref::Float64`: (デフォルト: `1.0`) 参照電力セットポイント（pu）、検証範囲: `(0, nothing)`
  * `ext::Dict{String, Any}`: (デフォルト: `Dict{String, Any}()`) ユーザーがシミュレーションで使用されないメタデータ（緯度や経度など）を追加するための[*ext*ra辞書](@ref additional_fields)。
  * `states::Vector{Symbol}`: (**変更しないでください。**) PIDGOVモデルの[状態](@ref S)は：

```
x_g1: フィルタされた入力測定値、
x_g2: PIブロック内部状態、
x_g3: 最初のレギュレーター状態、 
x_g4: 微分ブロック内部状態、 
x_g5: 2番目のレギュレーター状態、 
x_g6: ゲート位置状態、 
x_g7: 水の慣性状態
```

  * `n_states::Int`: (**変更しないでください。**) PIDGOVには7つの状態があります
  * `states_types::Vector{StateTypes}`: (**変更しないでください。**) PIDGOVには7つの[微分](@ref states_list) [状態](@ref S)があります
  * `internal::InfrastructureSystemsInternal`: (**変更しないでください。**) PowerSystems.jl内部参照
