```
mutable struct ST6B <: AVR
    OEL_Flag::Int
    Tr::Float64
    K_pa::Float64
    K_ia::Float64
    K_da::Float64
    T_da::Float64
    Va_lim::MinMax
    K_ff::Float64
    K_m::Float64
    K_ci::Float64
    K_lr::Float64
    I_lr::Float64
    Vr_lim::MinMax
    Kg::Float64
    Tg::Float64
    V_ref::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
    states_types::Vector{StateTypes}
    internal::InfrastructureSystemsInternal
end
```

これらの励磁システムでは、電圧（および複合システムの電流も）を適切なレベルに変換します。制御されたまたは制御されていない整流器が、発電機のフィールドに必要な直流を供給します。IEEE Std 421.5 タイプ ST6B 励磁システムのパラメータ。PSSEおよびPSLFにおけるST6B

# 引数

  * `OEL_Flag::Int`: ST6BのOELフラグ: 1: HVゲート前、2: HVゲート後、検証範囲: `(0, 2)`
  * `Tr::Float64`: レギュレータ入力フィルタ時間定数（秒）、検証範囲: `(0, nothing)`
  * `K_pa::Float64`: レギュレータ比例ゲイン、検証範囲: `(0, nothing)`
  * `K_ia::Float64`: レギュレータ積分ゲイン、検証範囲: `(0, nothing)`
  * `K_da::Float64`: レギュレータ微分ゲイン、検証範囲: `(0, nothing)`
  * `T_da::Float64`: 電圧レギュレータ微分チャネル時間定数（秒）、検証範囲: `(0, nothing)`
  * `Va_lim::MinMax`: レギュレータ出力制限（Vi*min, Vi*max）
  * `K_ff::Float64`: 内部ループフィールドレギュレータの前制御ゲイン、検証範囲: `(0, nothing)`
  * `K_m::Float64`: 内部ループフィールドレギュレータの前方ゲイン、検証範囲: `(0, nothing)`
  * `K_ci::Float64`: 励磁器出力電流制限調整ゲイン、検証範囲: `(0, nothing)`
  * `K_lr::Float64`: 励磁器出力電流制限器ゲイン、検証範囲: `(0, nothing)`
  * `I_lr::Float64`: 励磁器電流制限器基準、検証範囲: `(0, nothing)`
  * `Vr_lim::MinMax`: 電圧レギュレータ制限（Vi*min, Vi*max）
  * `Kg::Float64`: 内部ループフィールドレギュレータのフィードバックゲイン定数、検証範囲: `(0, nothing)`
  * `Tg::Float64`: 内部ループフィールド電圧レギュレータのフィードバック時間定数（秒）、検証範囲: `(0, nothing)`
  * `V_ref::Float64`: （デフォルト: `1.0`）基準電圧セットポイント（pu）、検証範囲: `(0, nothing)`
  * `ext::Dict{String, Any}`: （デフォルト: `Dict{String, Any}()`）シミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度。
  * `states::Vector{Symbol}`: (**変更しないでください。**) [状態](@ref S)は：

```
Vm: 感知された端子電圧、
x_i: レギュレータ積分器、
x_d: レギュレータ微分器、
Vg: レギュレータフィードバック
```

  * `n_states::Int`: (**変更しないでください。**) ST6Bは4つの状態を持ちます
  * `states_types::Vector{StateTypes}`: (**変更しないでください。**) ST6Bは4つの状態を持ちます
  * `internal::InfrastructureSystemsInternal`: (**変更しないでください。**) PowerSystems.jl内部参照
