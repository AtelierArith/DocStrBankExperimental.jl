```
mutable struct AVRTypeII <: AVR
    K0::Float64
    T1::Float64
    T2::Float64
    T3::Float64
    T4::Float64
    Te::Float64
    Tr::Float64
    Va_lim::MinMax
    Ae::Float64
    Be::Float64
    V_ref::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
    states_types::Vector{StateTypes}
    internal::InfrastructureSystemsInternal
end
```

自動電圧調整器タイプIIのパラメータ - 典型的な静的励磁器モデル

# 引数

  * `K0::Float64`: 調整器ゲイン、検証範囲: `(0, nothing)`
  * `T1::Float64`: sにおける第1極、検証範囲: `(0, nothing)`
  * `T2::Float64`: sにおける第1ゼロ、検証範囲: `(0, nothing)`
  * `T3::Float64`: sにおける第1極、検証範囲: `(0, nothing)`
  * `T4::Float64`: sにおける第1ゼロ、検証範囲: `(0, nothing)`
  * `Te::Float64`: sにおけるフィールド回路時間定数、検証範囲: `(0, nothing)`
  * `Tr::Float64`: sにおける電圧測定時間定数、検証範囲: `(0, nothing)`
  * `Va_lim::MinMax`: piコントローラの制限 `(Va_min, Va_max)`
  * `Ae::Float64`: 第1天井係数、検証範囲: `(0, nothing)`
  * `Be::Float64`: 第2天井係数、検証範囲: `(0, nothing)`
  * `V_ref::Float64`: (デフォルト: `1.0`) 参照電圧設定値 (pu)、検証範囲: `(0, nothing)`
  * `ext::Dict{String, Any}`: (デフォルト: `Dict{String, Any}()`) ユーザーがシミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度。
  * `states::Vector{Symbol}`: (**変更しないでください。**) [状態](@ref S)は次の通りです:

```
Vf: 電圧フィールド,
Vr1: 第1リードラグ状態,
Vr2: 第2リードラグ状態,
Vm: 測定電圧
```

  * `n_states::Int`: (**変更しないでください。**) AVRタイプIIは4つの状態を持ちます
  * `states_types::Vector{StateTypes}`: (**変更しないでください。**) AVRタイプIIは4つの[differential](@ref states_list) [状態](@ref S)を持ちます
  * `internal::InfrastructureSystemsInternal`: (**変更しないでください。**) PowerSystems.jl内部参照
