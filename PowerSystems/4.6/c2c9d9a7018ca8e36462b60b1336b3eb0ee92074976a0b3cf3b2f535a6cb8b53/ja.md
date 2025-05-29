```
mutable struct AVRTypeI <: AVR
    Ka::Float64
    Ke::Float64
    Kf::Float64
    Ta::Float64
    Te::Float64
    Tf::Float64
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

自動電圧調整器タイプIのパラメータ - IEEEタイプDC1に似ています

# 引数

  * `Ka::Float64`: 増幅器ゲイン、検証範囲: `(0, nothing)`
  * `Ke::Float64`: フィールド回路の積分偏差、検証範囲: `(0, nothing)`
  * `Kf::Float64`: 安定化器ゲイン（s * pu/pu）、検証範囲: `(0, nothing)`
  * `Ta::Float64`: 増幅器の時間定数（s）、検証範囲: `(0, nothing)`
  * `Te::Float64`: フィールド回路の時間定数（s）、検証範囲: `(0, nothing)`
  * `Tf::Float64`: 安定化器の時間定数（s）、検証範囲: `(0, nothing)`
  * `Tr::Float64`: 電圧測定の時間定数（s）、検証範囲: `(0, nothing)`
  * `Va_lim::MinMax`: PIコントローラーの制限 `(Va_min, Va_max)`
  * `Ae::Float64`: 1番目の天井係数、検証範囲: `(0, nothing)`
  * `Be::Float64`: 2番目の天井係数、検証範囲: `(0, nothing)`
  * `V_ref::Float64`: （デフォルト: `1.0`）基準電圧セットポイント（pu）、検証範囲: `(0, nothing)`
  * `ext::Dict{String, Any}`: （デフォルト: `Dict{String, Any}()`）ユーザーがシミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度。
  * `states::Vector{Symbol}`: (**変更しないでください。**) [状態](@ref S)は：

```
Vf: 電圧フィールド,
Vr1: 増幅器状態,
Vr2: 安定化フィードバック状態,
Vm: 測定電圧
```

  * `n_states::Int`: (**変更しないでください。**) AVRタイプIは4つの状態を持ちます
  * `states_types::Vector{StateTypes}`: (**変更しないでください。**) AVRタイプIは4つの[微分](@ref states_list) [状態](@ref S)を持ちます
  * `internal::InfrastructureSystemsInternal`: (**変更しないでください。**) PowerSystems.jl内部参照
