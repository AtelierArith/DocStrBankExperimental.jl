```
mutable struct ST8C <: AVR
    OEL_Flag::Int
    UEL_Flag::Int
    SCL_Flag::Int
    SW1_Flag::Int
    Tr::Float64
    K_pr::Float64
    K_ir::Float64
    Vpi_lim::MinMax
    K_pa::Float64
    K_ia::Float64
    Va_lim::MinMax
    K_a::Float64
    T_a::Float64
    Vr_lim::MinMax
    K_f::Float64
    T_f::Float64
    K_c1::Float64
    K_p::Float64
    K_i1::Float64
    X_l::Float64
    θ_p::Float64
    VB1_max::Float64
    K_c2::Float64
    K_i2::Float64
    VB2_max::Float64
    V_ref::Float64
    Ifd_ref::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
    states_types::Vector{StateTypes}
    internal::InfrastructureSystemsInternal
end
```

これらの励磁システムでは、電圧（および複合システムの電流も）を適切なレベルに変換します。整流器は、制御されたものと制御されていないもののいずれかで、発電機のフィールドに必要な直流を供給します。IEEE Std 421.5 Type ST8C励磁システムのパラメータ。PSSEおよびPSLFにおけるST8C

# 引数

  * `OEL_Flag::Int`: ST8CのOELフラグ: <2: 電圧エラーでの合計, 2: ゲートでのOEL引き継ぎ, 検証範囲: `(0, 2)`
  * `UEL_Flag::Int`: ST8CのUELフラグ: <2: 電圧エラーでの合計, 2: ゲートでのUEL引き継ぎ, 検証範囲: `(0, 2)`
  * `SCL_Flag::Int`: ST8CのSCLフラグ: <2: 電圧エラーでの合計, 2: UELおよびOELゲートでのSCL引き継ぎ, 検証範囲: `(0, 2)`
  * `SW1_Flag::Int`: ST8Cの電源選択器のSW1フラグ: <2: 発電機端子電圧からの電源, 2: 独立電源, 検証範囲: `(0, 2)`
  * `Tr::Float64`: レギュレータ入力フィルタの時間定数（秒単位）, 検証範囲: `(0, nothing)`
  * `K_pr::Float64`: レギュレータ比例ゲイン（pu）, 検証範囲: `(0, nothing)`
  * `K_ir::Float64`: レギュレータ積分ゲイン（pu）, 検証範囲: `(0, nothing)`
  * `Vpi_lim::MinMax`: レギュレータ入力制限（Vpi*min, Vpi*max）
  * `K_pa::Float64`: フィールド電流レギュレータの比例ゲイン（pu）, 検証範囲: `(0, nothing)`
  * `K_ia::Float64`: フィールド電流レギュレータの積分ゲイン（pu）, 検証範囲: `(0, nothing)`
  * `Va_lim::MinMax`: フィールド電流レギュレータ出力制限（Va*min, Va*max）
  * `K_a::Float64`: フィールド電流レギュレータの比例ゲイン（pu）, 検証範囲: `(0, nothing)`
  * `T_a::Float64`: 制御整流器ブリッジの等価時間定数（秒単位）, 検証範囲: `(0, nothing)`
  * `Vr_lim::MinMax`: 電圧レギュレータ制限（Vr*min, Vr*max）
  * `K_f::Float64`: 励磁フィールド電流フィードバックゲイン（pu）, 検証範囲: `(0, nothing)`
  * `T_f::Float64`: フィールド電流フィードバックの時間定数（秒単位）, 検証範囲: `(0, nothing)`
  * `K_c1::Float64`: 整流器の負荷係数（コミュテーションリアクタンスに比例）（pu）, 検証範囲: `(0, nothing)`
  * `K_p::Float64`: ポテンシャル回路（電圧）ゲイン係数（pu）, 検証範囲: `(0, nothing)`
  * `K_i1::Float64`: ポテンシャル回路（電流）ゲイン係数（pu）, 検証範囲: `(0, nothing)`
  * `X_l::Float64`: ポテンシャルソースに関連するリアクタンス（pu）, 検証範囲: `(0, nothing)`
  * `θ_p::Float64`: ポテンシャル回路の位相角（度）, 検証範囲: `(0, nothing)`
  * `VB1_max::Float64`: 利用可能な最大励磁電圧（pu）, 検証範囲: `(0, nothing)`
  * `K_c2::Float64`: 整流器の負荷係数（コミュテーションリアクタンスに比例）（pu）, 検証範囲: `(0, nothing)`
  * `K_i2::Float64`: ポテンシャル回路（電流）ゲイン係数（pu）, 検証範囲: `(0, nothing)`
  * `VB2_max::Float64`: 利用可能な最大励磁電圧（pu）, 検証範囲: `(0, nothing)`
  * `V_ref::Float64`: （デフォルト: `1.0`）基準電圧セットポイント（pu）, 検証範囲: `(0, nothing)`
  * `Ifd_ref::Float64`: （デフォルト: `1.0`）基準フィールド電流セットポイント（pu）, 検証範囲: `(0, nothing)`
  * `ext::Dict{String, Any}`: （デフォルト: `Dict{String, Any}()`）ユーザーがシミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度。
  * `states::Vector{Symbol}`: (**変更しないでください。**) [states](@ref S) は:

```
Vm: 感知された端子電圧,
x_a1: レギュレータ積分器の状態,
x_a2: フィールド電流レギュレータの状態,
x_a3: コントローラ整流器ブリッジの状態,
x_a4: レギュレータフィードバックの状態
```

  * `n_states::Int`: (**変更しないでください。**) ST8Cは5つの状態を持ちます
  * `states_types::Vector{StateTypes}`: (**変更しないでください。**) ST8Cは5つの状態を持ちます
  * `internal::InfrastructureSystemsInternal`: (**変更しないでください。**) PowerSystems.jl内部参照
