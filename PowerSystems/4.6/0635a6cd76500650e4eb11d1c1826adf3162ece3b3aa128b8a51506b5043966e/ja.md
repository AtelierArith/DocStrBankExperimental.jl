```
mutable struct ESST1A <: AVR
    UEL_flags::Int
    PSS_flags::Int
    Tr::Float64
    Vi_lim::Tuple{Float64, Float64}
    Tc::Float64
    Tb::Float64
    Tc1::Float64
    Tb1::Float64
    Ka::Float64
    Ta::Float64
    Va_lim::MinMax
    Vr_lim::MinMax
    Kc::Float64
    Kf::Float64
    Tf::Float64
    K_lr::Float64
    I_lr::Float64
    V_ref::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
    states_types::Vector{StateTypes}
    internal::InfrastructureSystemsInternal
end
```

この励磁システムは、発電機端子からトランスを介して電力を供給し、制御整流器（サイリスタ経由）によって調整されます。IEEE Std 421.5 タイプ ST1A 励磁システムのパラメータ。PSSEおよびPSLFにおけるESST1A

# 引数

  * `UEL_flags::Int`: 過小励磁制限器（UEL）エントリのコード入力。サポートされていない、検証範囲: `(1, 3)`
  * `PSS_flags::Int`: 電力システム安定化装置（PSS）または（VOS）エントリのコード入力、検証範囲: `(1, 2)`
  * `Tr::Float64`: レギュレータ入力フィルタ時間定数（秒）、検証範囲: `(0, 0.1)`
  * `Vi_lim::Tuple{Float64, Float64}`: 電圧誤差制限（レギュレータ入力）（Vi*min, Vi*max）
  * `Tc::Float64`: 最初のレギュレータ分母（リード）時間定数（秒）、検証範囲: `(0, 10)`
  * `Tb::Float64`: 最初のレギュレータ分母（ラグ）時間定数（秒）、検証範囲: `(0, 20)`
  * `Tc1::Float64`: 2番目のレギュレータ分母（リード）時間定数（秒）、検証範囲: `(0, 10)`
  * `Tb1::Float64`: 2番目のレギュレータ分母（ラグ）時間定数（秒）、検証範囲: `(0, 20)`
  * `Ka::Float64`: 電圧レギュレータゲイン、検証範囲: `(50, 1000)`
  * `Ta::Float64`: 電圧レギュレータ時間定数（秒）、検証範囲: `(0, 0.5)`
  * `Va_lim::MinMax`: レギュレータ出力の制限 `(Va_min, Va_max)`
  * `Vr_lim::MinMax`: 励磁器出力の制限 `(Vr_min, Vr_max)`
  * `Kc::Float64`: 整流器負荷係数（コミュテーションリアクタンスに比例）、検証範囲: `(0, 0.3)`
  * `Kf::Float64`: レートフィードバックゲイン、検証範囲: `(0, 0.3)`
  * `Tf::Float64`: レートフィードバック時間定数（秒）、検証範囲: `(eps(), 1.5)`
  * `K_lr::Float64`: 励磁器出力電流制限器ゲイン、検証範囲: `(0, 5)`
  * `I_lr::Float64`: 励磁器出力電流制限参照、検証範囲: `(0, 5)`
  * `V_ref::Float64`: （デフォルト: `1.0`）基準電圧セットポイント（pu）、検証範囲: `(0, nothing)`
  * `ext::Dict{String, Any}`: （デフォルト: `Dict{String, Any}()`) ユーザーがシミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度。
  * `states::Vector{Symbol}`: (**変更しないでください。**) [状態](@ref S) は：

```
Vm: 感知された端子電圧,
Vr1: 最初のリードラグ状態,
Vr2: 2番目のリードラグ状態,
Va: レギュレータ出力状態,
Vr3: フィードバック出力状態
```

  * `n_states::Int`: (**変更しないでください。**) ST1Aは5つの状態を持ちます
  * `states_types::Vector{StateTypes}`: (**変更しないでください。**) ST1Aは5つの状態を持ちます
  * `internal::InfrastructureSystemsInternal`: (**変更しないでください。**) PowerSystems.jl内部参照
