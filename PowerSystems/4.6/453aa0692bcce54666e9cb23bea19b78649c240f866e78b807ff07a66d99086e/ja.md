```
mutable struct ESDC2A <: AVR
    Tr::Float64
    Ka::Float64
    Ta::Float64
    Tb::Float64
    Tc::Float64
    Vr_lim::MinMax
    Ke::Float64
    Te::Float64
    Kf::Float64
    Tf::Float64
    switch::Int
    E_sat::Tuple{Float64, Float64}
    Se::Tuple{Float64, Float64}
    V_ref::Float64
    saturation_coeffs::Tuple{Float64, Float64}
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
    states_types::Vector{StateTypes}
    internal::InfrastructureSystemsInternal
end
```

フィールド制御された直流コミュテータ励磁装置を表すために使用され、発電機または補助バスから派生した電源を持つ連続動作の電圧レギュレータを備えています。IEEE Std 421.5 タイプ DC2A 励磁システムのパラメータ。このモデルは、PSSEおよびPSLFのESDC2Aに対応しています。

# 引数

  * `Tr::Float64`: 電圧測定時間定数（秒）、検証範囲: `(0, 0.5)`
  * `Ka::Float64`: 増幅器ゲイン、検証範囲: `(10, 500)`
  * `Ta::Float64`: 増幅器時間定数（秒）、検証範囲: `(0, 1)`
  * `Tb::Float64`: レギュレータ入力時間定数（秒）、検証範囲: `(0, nothing)`
  * `Tc::Float64`: レギュレータ入力時間定数（秒）、検証範囲: `(0, nothing)`
  * `Vr_lim::MinMax`: 電圧レギュレータの制限（レギュレータ出力）（Vi*min, Vi*max）
  * `Ke::Float64`: 自励フィールドに関連する励磁器定数、検証範囲: `(-1, 1)`
  * `Te::Float64`: 励磁器時間定数、励磁器制御に関連する統合率、検証範囲: `(eps(), 2)`
  * `Kf::Float64`: 励磁制御システム安定化器ゲイン、検証範囲: `(0, 0.3)`
  * `Tf::Float64`: 励磁制御システム安定化器時間定数。適切なデータ: 5.0 <= Tf/Kf <= 15.0、検証範囲: `(eps(), 1.5)`
  * `switch::Int`: スイッチ、検証範囲: `(0, 1)`
  * `E_sat::Tuple{Float64, Float64}`: 飽和係数に対する励磁器出力電圧: (E1, E2)
  * `Se::Tuple{Float64, Float64}`: 励磁器出力電圧における励磁器飽和係数: (Se(E1), Se(E2))
  * `V_ref::Float64`: (デフォルト: `1.0`) 参照電圧設定値（pu）、検証範囲: `(0, nothing)`
  * `saturation_coeffs::Tuple{Float64, Float64}`: (デフォルト: `PowerSystems.get_avr_saturation(E_sat, Se)`) (**変更しないでください。**) 関数の係数 (A,B): Se(V) = B(V - A)^2/V
  * `ext::Dict{String, Any}`: (デフォルト: `Dict{String, Any}()`) ユーザーがシミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度。
  * `states::Vector{Symbol}`: (**変更しないでください。**) [状態](@ref S) は:

```
Vt: 端子電圧,
Vr1: 入力リード遅れ,
Vr2: レギュレータ出力,
Vf: 励磁器出力, 
Vr3: レートフィードバック積分器
```

  * `n_states::Int`: (**変更しないでください。**) ESDC2Aは5つの状態を持ちます
  * `states_types::Vector{StateTypes}`: (**変更しないでください。**) ESDC2Aは5つの[differential](@ref states_list) [状態](@ref S)を持ちます
  * `internal::InfrastructureSystemsInternal`: (**変更しないでください。**) PowerSystems.jl内部参照
