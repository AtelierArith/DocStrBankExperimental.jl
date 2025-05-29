```
mutable struct ESDC1A <: AVR
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

自己励起シャントフィールドで、電圧レギュレーターが一般にバッカーブーストと呼ばれるモードで動作します。 IEEE Std 421.5 Type DC1A励起システムのパラメータ。このモデルはPSSEおよびPSLFのESDC1Aに対応します。

# 引数

  * `Tr::Float64`: 電圧測定時間定数（秒）、検証範囲: `(0, 0.5)`
  * `Ka::Float64`: 増幅器ゲイン、検証範囲: `(10, 500)`
  * `Ta::Float64`: 増幅器時間定数（秒）、検証範囲: `(0, 1)`
  * `Tb::Float64`: レギュレーター入力時間定数（秒）、検証範囲: `(0, nothing)`
  * `Tc::Float64`: レギュレーター入力時間定数（秒）、検証範囲: `(0, nothing)`
  * `Vr_lim::MinMax`: 電圧レギュレーターの制限（レギュレーター出力）（Vi*min, Vi*max）
  * `Ke::Float64`: 自己励起フィールドに関連する励起器定数、検証範囲: `(0, nothing)`
  * `Te::Float64`: 励起器時間定数、励起器制御に関連する統合率、検証範囲: `(eps(), 1)`
  * `Kf::Float64`: 励起制御システム安定化器ゲイン、検証範囲: `(eps(), 0.3)`
  * `Tf::Float64`: 励起制御システム安定化器時間定数、検証範囲: `(eps(), nothing)`
  * `switch::Int`: スイッチ、検証範囲: `(0, 1)`
  * `E_sat::Tuple{Float64, Float64}`: 飽和係数に対する励起器出力電圧: (E1, E2)
  * `Se::Tuple{Float64, Float64}`: 励起器出力電圧における励起器飽和係数: (Se(E1), Se(E2))
  * `V_ref::Float64`: (デフォルト: `1.0`) 参照電圧設定値（pu）、検証範囲: `(0, nothing)`
  * `saturation_coeffs::Tuple{Float64, Float64}`: (デフォルト: `PowerSystems.get_avr_saturation(E_sat, Se)`) (**変更しないでください。**) 関数の係数 (A,B): Se(V) = B(V - A)^2/V
  * `ext::Dict{String, Any}`: (デフォルト: `Dict{String, Any}()`) ユーザーがシミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度。
  * `states::Vector{Symbol}`: (**変更しないでください。**) [状態](@ref S)は次のとおりです:

```
Vt: ターミナル電圧,
Vr1: 入力リード遅れ,
Vr2: レギュレーター出力,
Vf: 励起器出力, 
Vr3: レートフィードバック積分器
```

  * `n_states::Int`: (**変更しないでください。**) ESDC1Aは5つの状態を持ちます
  * `states_types::Vector{StateTypes}`: (**変更しないでください。**) ESDC1Aは5つの[differential](@ref states_list) [状態](@ref S)を持ちます
  * `internal::InfrastructureSystemsInternal`: (**変更しないでください。**) PowerSystems.jl内部参照
