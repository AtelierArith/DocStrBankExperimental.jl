```
mutable struct EXPIC1 <: AVR
    Tr::Float64
    Ka::Float64
    Ta::Float64
    Va_lim::MinMax
    Ta_2::Float64
    Ta_3::Float64
    Ta_4::Float64
    Vr_lim::MinMax
    Kf::Float64
    Tf_1::Float64
    Tf_2::Float64
    Efd_lim::MinMax
    Ke::Float64
    Te::Float64
    E_sat::Tuple{Float64, Float64}
    Se::Tuple{Float64, Float64}
    Kp::Float64
    Ki::Float64
    Kc::Float64
    V_ref::Float64
    saturation_coeffs::Tuple{Float64, Float64}
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
    states_types::Vector{StateTypes}
    internal::InfrastructureSystemsInternal
end
```

一般的な比例/積分励起システム

# 引数

  * `Tr::Float64`: 規制器入力フィルタの時間定数（秒）、検証範囲: `(0, 0.5)`
  * `Ka::Float64`: 電圧規制器のゲイン、検証範囲: `(1, 500)`
  * `Ta::Float64`: 電圧規制器の時間定数（秒）、検証範囲: `(0, 10)`
  * `Va_lim::MinMax`: PIコントローラの制限 `(Vr_min, Vr_max)`
  * `Ta_2::Float64`: 電圧規制器の時間定数（秒）、検証範囲: `(0, nothing)`
  * `Ta_3::Float64`: 電圧規制器の時間定数（秒）、検証範囲: `(0, nothing)`
  * `Ta_4::Float64`: 電圧規制器の時間定数（秒）、検証範囲: `(0, nothing)`
  * `Vr_lim::MinMax`: 電圧規制器の制限（規制器出力）(Vi*min, Vi*max)
  * `Kf::Float64`: レートフィードバックゲイン、検証範囲: `(0, 0.3)`
  * `Tf_1::Float64`: レートフィードバックの時間定数（秒）、検証範囲: `(eps(), 15)`
  * `Tf_2::Float64`: レートフィードバックの時間定数（秒）、検証範囲: `(0, 5)`
  * `Efd_lim::MinMax`: フィールド電圧規制器の制限（規制器出力）(Efd*min, Efd*max)
  * `Ke::Float64`: 励起器定数、検証範囲: `(0, 1)`
  * `Te::Float64`: 励起器の時間定数、検証範囲: `(0, 2)`
  * `E_sat::Tuple{Float64, Float64}`: 飽和係数のための励起器出力電圧: (E1, E2)
  * `Se::Tuple{Float64, Float64}`: 励起器出力電圧における励起器の飽和係数: (Se(E1), Se(E2))
  * `Kp::Float64`: 潜在的なソースゲイン、検証範囲: `(0, 5)`
  * `Ki::Float64`: 現在のソースゲイン、検証範囲: `(0, 1.1)`
  * `Kc::Float64`: 励起器の調整係数、検証範囲: `(0, 2)`
  * `V_ref::Float64`: (デフォルト: `1.0`) 参照電圧設定値（pu）、検証範囲: `(0, nothing)`
  * `saturation_coeffs::Tuple{Float64, Float64}`: (デフォルト: `PowerSystems.get_avr_saturation(E_sat, Se)`) (**変更しないでください。**) 関数の係数 (A,B): Se(V) = B(V - A)^2/V
  * `ext::Dict{String, Any}`: (デフォルト: `Dict{String, Any}()`) ユーザーがシミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度。
  * `states::Vector{Symbol}`: (**変更しないでください。**) [状態](@ref S) は:

```
Vm: 感知された端子電圧,
Vr1: 最初のリードラグ状態,
Vr2: 第二の規制器リードラグ状態,
Vr2: 第三の規制器リードラグ状態 
Vf: 励起器出力 
Vr3: 最初のフィードバック積分器,
Vr4: 第二のフィードバック積分器
```

  * `n_states::Int`: (**変更しないでください。**) EXPIC1は6つの状態を持つ
  * `states_types::Vector{StateTypes}`: (**変更しないでください。**) EXPICは6つの状態を持つ
  * `internal::InfrastructureSystemsInternal`: (**変更しないでください。**) PowerSystems.jl内部参照
