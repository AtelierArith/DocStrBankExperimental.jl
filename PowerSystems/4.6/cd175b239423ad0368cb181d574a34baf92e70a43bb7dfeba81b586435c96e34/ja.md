```
mutable struct ZeroOrderBESS <: DCSource
    rated_voltage::Float64
    rated_current::Float64
    battery_voltage::Float64
    battery_resistance::Float64
    dc_dc_inductor::Float64
    dc_link_capacitance::Float64
    fs::Float64
    kpv::Float64
    kiv::Float64
    kpi::Float64
    kii::Float64
    Vdc_ref::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
end
```

バッテリーエネルギー貯蔵システムを持つDC側のパラメータは、["Grid-Coupled Dynamic Response of Battery-Driven Voltage Source Converters."](https://arxiv.org/abs/2007.11776)からのものです。

# 引数

  * `rated_voltage::Float64`: 定格電圧 (V)、検証範囲: `(0, nothing)`
  * `rated_current::Float64`: 定格電流 (A)、検証範囲: `(0, nothing)`
  * `battery_voltage::Float64`: バッテリー電圧のpu ([`DEVICE_BASE`](@ref per_unit))、検証範囲: `(0, nothing)`
  * `battery_resistance::Float64`: バッテリー抵抗のpu ([`DEVICE_BASE`](@ref per_unit))、検証範囲: `(0, nothing)`
  * `dc_dc_inductor::Float64`: DC/DCインダクタンスのpu ([`DEVICE_BASE`](@ref per_unit))、検証範囲: `(0, nothing)`
  * `dc_link_capacitance::Float64`: DCリンクキャパシタンスのpu ([`DEVICE_BASE`](@ref per_unit))、検証範囲: `(0, nothing)`
  * `fs::Float64`: DC/DCコンバータのスイッチング周波数 (kHz)、検証範囲: `(0, nothing)`
  * `kpv::Float64`: 電圧制御器の比例ゲイン、検証範囲: `(0, nothing)`
  * `kiv::Float64`: 電圧制御器の積分ゲイン、検証範囲: `(0, nothing)`
  * `kpi::Float64`: 電流制御器の比例ゲイン、検証範囲: `(0, nothing)`
  * `kii::Float64`: 電流制御器の積分ゲイン、検証範囲: `(0, nothing)`
  * `Vdc_ref::Float64`: (デフォルト: `1.1`) 参照DC電圧セットポイントのpu ([`DEVICE_BASE`](@ref per_unit))、検証範囲: `(0, nothing)`
  * `ext::Dict{String, Any}`: (デフォルト: `Dict{String, Any}()`) シミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度など。
  * `states::Vector{Symbol}`: (**変更しないでください。**) ZeroOrderBESSモデルの[状態](@ref S)は次の通りです：

```
v_dc: DCリンク電圧、
i_b: バッテリー電流、
 ν: 電圧制御器の積分器状態、
 ζ: PI電流制御器の積分器状態
```

  * `n_states::Int`: (**変更しないでください。**) ZeroOrderBESSは4つの状態を持ちます。
