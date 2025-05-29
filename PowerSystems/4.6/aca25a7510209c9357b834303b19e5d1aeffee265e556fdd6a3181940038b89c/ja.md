```
mutable struct ESAC1A <: AVR
    Tr::Float64
    Tb::Float64
    Tc::Float64
    Ka::Float64
    Ta::Float64
    Va_lim::MinMax
    Te::Float64
    Kf::Float64
    Tf::Float64
    Kc::Float64
    Kd::Float64
    Ke::Float64
    E_sat::Tuple{Float64, Float64}
    Se::Tuple{Float64, Float64}
    Vr_lim::MinMax
    V_ref::Float64
    saturation_coeffs::Tuple{Float64, Float64}
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
    states_types::Vector{StateTypes}
    internal::InfrastructureSystemsInternal
end
```

この励磁システムは、制御されていない整流器を介して出力を供給する発電機の主励磁装置で構成されています。励磁装置は自己励磁を使用せず、電圧調整器の電力は外部の過渡現象に影響されないソースから取得されます。IEEE Std 421.5 Type AC1A励磁システムのパラメータ。このモデルはPSSEおよびPSLFのESAC1Aに対応しています。

# 引数

  * `Tr::Float64`: 調整器入力フィルターの時間定数（秒）、検証範囲: `(0, 0.5)`
  * `Tb::Float64`: 調整器の分母（遅れ）時間定数（秒）、検証範囲: `(0, 20)`
  * `Tc::Float64`: 調整器の分子（先行）時間定数（秒）、検証範囲: `(0, 20)`
  * `Ka::Float64`: 調整器出力ゲイン、検証範囲: `(0, 1000)`
  * `Ta::Float64`: 調整器出力時間定数（秒）、検証範囲: `(0, 10)`
  * `Va_lim::MinMax`: 調整器出力の制限 `(Va_min, Va_max)`
  * `Te::Float64`: 励磁装置のフィールド時間定数（秒）、検証範囲: `(eps(), 2)`
  * `Kf::Float64`: レートフィードバック励磁システム安定化器ゲイン、検証範囲: `(0, 0.3)`
  * `Tf::Float64`: レートフィードバック時間定数、検証範囲: `(eps(), 1.5)`
  * `Kc::Float64`: 整流器の負荷係数（通過リアクタンスに比例）、検証範囲: `(0, 1)`
  * `Kd::Float64`: 励磁装置の発電機リアクタンスの関数である脱磁係数、検証範囲: `(0, 1)`
  * `Ke::Float64`: 励磁装置フィールドの比例定数、検証範囲: `(0, 1)`
  * `E_sat::Tuple{Float64, Float64}`: 飽和係数に対する励磁装置出力電圧: (E1, E2)
  * `Se::Tuple{Float64, Float64}`: 励磁装置出力電圧における励磁装置の飽和係数: (Se(E1), Se(E2))
  * `Vr_lim::MinMax`: 励磁装置フィールド電圧の制限: `(Vr_min, Vr_max)`
  * `V_ref::Float64`: (デフォルト: `1.0`) 参照電圧設定値 (pu)、検証範囲: `(0, nothing)`
  * `saturation_coeffs::Tuple{Float64, Float64}`: (デフォルト: `PowerSystems.get_avr_saturation(E_sat, Se)`) (**変更しないでください。**) 関数の係数 (A,B): Se(x) = B(x - A)^2/x
  * `ext::Dict{String, Any}`: (デフォルト: `Dict{String, Any}()`) ユーザーがシミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度など。
  * `states::Vector{Symbol}`: (**変更しないでください。**) [状態](@ref S)は次のとおりです:

```
Vm: 感知された端子電圧,
Vr1: リード-ラグ状態,
Vr2: 調整器出力状態,
Ve: 積分器出力状態,
Vr3: フィードバック出力状態
```

  * `n_states::Int`: (**変更しないでください。**) ESAC1Aは5つの状態を持ちます
  * `states_types::Vector{StateTypes}`: (**変更しないでください。**) ESAC1Aは5つの状態を持ちます
  * `internal::InfrastructureSystemsInternal`: (**変更しないでください。**) PowerSystems.jl内部参照
