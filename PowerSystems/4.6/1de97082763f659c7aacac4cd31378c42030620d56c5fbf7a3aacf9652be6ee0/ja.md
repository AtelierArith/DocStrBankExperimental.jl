```
mutable struct ESST4B <: AVR
    Tr::Float64
    K_pr::Float64
    K_ir::Float64
    Vr_lim::MinMax
    Ta::Float64
    K_pm::Float64
    K_im::Float64
    Vm_lim::MinMax
    Kg::Float64
    Kp::Float64
    Ki::Float64
    VB_max::Float64
    Kc::Float64
    Xl::Float64
    θp::Float64
    V_ref::Float64
    θp_rad::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
    states_types::Vector{StateTypes}
    internal::InfrastructureSystemsInternal
end
```

これらの励磁システムでは、電圧（および複合システムの電流）を適切なレベルに変換します。制御されたまたは制御されていない整流器が、発電機フィールドに必要な直流を供給します。IEEE Std 421.5 Type ST4B励磁システムのパラメータ。PSSEおよびPSLFのESST4B

# 引数

  * `Tr::Float64`: レギュレータ入力フィルタ時間定数（秒）、検証範囲: `(0, 0.5)`
  * `K_pr::Float64`: レギュレータ比例ゲイン、検証範囲: `(0, 75)`
  * `K_ir::Float64`: レギュレータ積分ゲイン、検証範囲: `(0, 75)`
  * `Vr_lim::MinMax`: 電圧レギュレータの制限（Vi*min, Vi*max）
  * `Ta::Float64`: 電圧レギュレータ時間定数（秒）、検証範囲: `(0, 1)`
  * `K_pm::Float64`: 電圧レギュレータ比例ゲイン出力、検証範囲: `(0, 1.2)`
  * `K_im::Float64`: 電圧レギュレータ積分ゲイン出力、検証範囲: `(0, 18)`
  * `Vm_lim::MinMax`: 内部ループ出力の制限（Vm*min, Vm*max）
  * `Kg::Float64`: 内部ループフィールドレギュレータのフィードバックゲイン定数、検証範囲: `(0, 1.1)`
  * `Kp::Float64`: ポテンシャル回路（電圧）ゲイン係数、検証範囲: `(0, 10)`
  * `Ki::Float64`: 複合回路（電流）ゲイン係数、検証範囲: `(0, 1.1)`
  * `VB_max::Float64`: 利用可能な最大励磁電圧、検証範囲: `(1, 20)`
  * `Kc::Float64`: コミュテーションリアクタンスに比例する整流器負荷係数、検証範囲: `(0, 1)`
  * `Xl::Float64`: ポテンシャルソースに関連するリアクタンス、検証範囲: `(0, 0.5)`
  * `θp::Float64`: ポテンシャル回路位相角（度）、検証範囲: `(-90, 90)`
  * `V_ref::Float64`: （デフォルト: `1.0`）基準電圧セットポイント（pu）、検証範囲: `(0, nothing)`
  * `θp_rad::Float64`: （デフォルト: `θp*π*inv(180)`）(**変更しないでください。**) ポテンシャル回路位相角（ラジアン）
  * `ext::Dict{String, Any}`: （デフォルト: `Dict{String, Any}()`）シミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度。
  * `states::Vector{Symbol}`: (**変更しないでください。**) [states](@ref S) は：

```
Vm: 感知された端子電圧,
Vt: 感知された端子電圧,
Vr1: レギュレータ積分器,
Vr2: レギュレータ出力,
Vm: 出力積分器
```

  * `n_states::Int`: (**変更しないでください。**) ST4Bは4つの状態を持ちます
  * `states_types::Vector{StateTypes}`: (**変更しないでください。**) ST4Bは4つの状態を持ちます
  * `internal::InfrastructureSystemsInternal`: (**変更しないでください。**) PowerSystems.jl内部参照
