```
mutable struct ActiveConstantPowerLoad <: DynamicInjection
    name::String
    r_load::Float64
    c_dc::Float64
    rf::Float64
    lf::Float64
    cf::Float64
    rg::Float64
    lg::Float64
    kp_pll::Float64
    ki_pll::Float64
    kpv::Float64
    kiv::Float64
    kpc::Float64
    kic::Float64
    base_power::Float64
    ext::Dict{String, Any}
    P_ref::Float64
    Q_ref::Float64
    V_ref::Float64
    ω_ref::Float64
    is_filter_differential::Int
    states::Vector{Symbol}
    n_states::Int
    internal::InfrastructureSystemsInternal
end
```

12-[states](@ref S) のアクティブパワーロードのパラメータは、["Dynamic Stability of a Microgrid With an Active Load."](https://doi.org/10.1109/TPEL.2013.2241455) に基づいています。

# 引数

  * `name::String`: コンポーネントの名前。同じタイプのコンポーネント（例：`PowerLoad`）はユニークな名前を持つ必要がありますが、異なるタイプのコンポーネント（例：`PowerLoad` と `ACBus`）は同じ名前を持つことができます。
  * `r_load::Float64`: DC側抵抗、検証範囲: `(0, nothing)`
  * `c_dc::Float64`: DC側キャパシタ、検証範囲: `(0, nothing)`
  * `rf::Float64`: コンバータ側フィルタ抵抗、検証範囲: `(0, nothing)`
  * `lf::Float64`: コンバータ側フィルタインダクタンス、検証範囲: `(0, nothing)`
  * `cf::Float64`: ACコンバータフィルタキャパシタンス、検証範囲: `(0, nothing)`
  * `rg::Float64`: ネットワーク側フィルタ抵抗、検証範囲: `(0, nothing)`
  * `lg::Float64`: ネットワーク側フィルタインダクタンス、検証範囲: `(0, nothing)`
  * `kp_pll::Float64`: PI-PLLブロックの比例定数、検証範囲: `(0, nothing)`
  * `ki_pll::Float64`: PI-PLLブロックの積分定数、検証範囲: `(0, nothing)`
  * `kpv::Float64`: 電圧制御ブロックの比例定数、検証範囲: `(0, nothing)`
  * `kiv::Float64`: 電圧制御ブロックの積分定数、検証範囲: `(0, nothing)`
  * `kpc::Float64`: 電流制御ブロックの比例定数、検証範囲: `(0, nothing)`
  * `kic::Float64`: 電流制御ブロックの積分定数、検証範囲: `(0, nothing)`
  * `base_power::Float64`: ユニットの基準電力 (MVA) [パーユニット化](@ref per_unit) のための、検証範囲: `(0, nothing)`
  * `ext::Dict{String, Any}`: (デフォルト: `Dict{String, Any}()`) シミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度など。
  * `P_ref::Float64`: 参照アクティブパワー (pu)
  * `Q_ref::Float64`: 参照リアクティブパワー (pu)
  * `V_ref::Float64`: 参照電圧 (pu)
  * `ω_ref::Float64`: 参照周波数 (pu)
  * `is_filter_differential::Int`: フィルタの[states](@ref S)が微分か代数かを決定するためのブール値
  * `states::Vector{Symbol}`: (**変更しないでください。**) [states](@ref S) は次の通りです：

```
θ_pll: PLL偏差角, 
ϵ_pll: PLL積分器状態, 
η: DC電圧制御器積分器状態, 
v_dc: キャパシタのDC電圧, 
γd: d軸電流制御器積分器状態, 
γq: q軸電流制御器積分器状態, 
ir_cnv: コンバータからの実電流,
ii_cnv: コンバータからの虚電流,
vr_filter: フィルタのキャパシタの実電圧,
vi_filter: フィルタのキャパシタの虚電圧,
ir_filter: フィルタからの実電流,
ii_filter: フィルタからの虚電流
```

  * `n_states::Int`: (**変更しないでください。**) ActiveConstantPowerLoad は 12 の状態を持ちます
  * `internal::InfrastructureSystemsInternal`: (**変更しないでください。**) PowerSystems.jl 内部参照
