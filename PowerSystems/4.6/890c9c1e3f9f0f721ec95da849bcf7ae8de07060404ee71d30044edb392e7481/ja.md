```
mutable struct IEEET1 <: AVR
    Tr::Float64
    Ka::Float64
    Ta::Float64
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

1968 IEEEタイプ1励磁システムモデル

# 引数

  * `Tr::Float64`: 電圧測定時間定数（秒）、検証範囲: `(0, 0.5)`
  * `Ka::Float64`: 増幅器ゲイン、検証範囲: `(10, 500)`
  * `Ta::Float64`: 増幅器時間定数（秒）、検証範囲: `(0, 1)`
  * `Vr_lim::MinMax`: 電圧調整器の制限（調整器出力）（Vi*min, Vi*max）
  * `Ke::Float64`: 自励フィールドに関連する励磁器定数、検証範囲: `(-1, 1)`
  * `Te::Float64`: 励磁器時間定数、励磁器制御に関連する統合率、検証範囲: `(eps(), 1)`
  * `Kf::Float64`: 励起制御システム安定化器ゲイン、検証範囲: `(eps(), 0.3)`
  * `Tf::Float64`: 励起制御システム安定化器時間定数。適切なデータ: 5 <= Tf/Kf <= 15、検証範囲: `(eps(), nothing)`
  * `switch::Int`: スイッチ、検証範囲: `(0, 1)`
  * `E_sat::Tuple{Float64, Float64}`: 飽和係数に対する励磁器出力電圧: (E1, E2)
  * `Se::Tuple{Float64, Float64}`: 励磁器出力電圧における励磁器飽和係数: (Se(E1), Se(E2))
  * `V_ref::Float64`: (デフォルト: `1.0`) 参照電圧設定値（pu）、検証範囲: `(0, nothing)`
  * `saturation_coeffs::Tuple{Float64, Float64}`: (デフォルト: `PowerSystems.get_avr_saturation(E_sat, Se)`) (**変更しないでください。**) 関数の係数 (A,B): Se(V) = B(V - A)^2/V
  * `ext::Dict{String, Any}`: (デフォルト: `Dict{String, Any}()`) ユーザーがシミュレーションで使用されないメタデータ（緯度や経度など）を追加するための[*ext*ra辞書](@ref additional_fields)。
  * `states::Vector{Symbol}`: (**変更しないでください。**) [状態](@ref S)は次のとおりです:

```
Vt: 端子電圧,
Vr: 調整器出力,
Vf: 励磁器出力, 
Vr3: レートフィードバック積分器
```

  * `n_states::Int`: (**変更しないでください。**) IEEET1は4つの状態を持っています
  * `states_types::Vector{StateTypes}`: (**変更しないでください。**) IEEET1 Iは4つの[differential](@ref states_list) [状態](@ref S)を持っています
  * `internal::InfrastructureSystemsInternal`: (**変更しないでください。**) PowerSystems.jl内部参照
