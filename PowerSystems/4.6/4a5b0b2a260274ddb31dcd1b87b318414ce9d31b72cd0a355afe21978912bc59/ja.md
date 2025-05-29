```
mutable struct DEGOV <: TurbineGov
    T1::Float64
    T2::Float64
    T3::Float64
    K::Float64
    T4::Float64
    T5::Float64
    T6::Float64
    Td::Float64
    P_ref::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
    states_types::Vector{StateTypes}
    internal::InfrastructureSystemsInternal
end
```

ウッドワードディーゼルガバナーモデルのパラメータ。DEGOV in PowerWorld

# 引数

  * `T1::Float64`: ガバナーメカニズムの時間定数、検証範囲: `(eps(), 100)`
  * `T2::Float64`: タービンパワーの時間定数、検証範囲: `(eps(), 100)`
  * `T3::Float64`: タービン排気温度の時間定数、検証範囲: `(eps(), 100)`
  * `K::Float64`: ガバナーゲイン（ドロップの逆数）、検証範囲: `(eps(), 100)`
  * `T4::Float64`: ガバナーリード時間定数、検証範囲: `(eps(), 100)`
  * `T5::Float64`: ガバナーラグ時間定数、検証範囲: `(eps(), 100)`
  * `T6::Float64`: アクチュエーターの時間定数、検証範囲: `(eps(), 100)`
  * `Td::Float64`: エンジンの時間遅延、検証範囲: `(eps(), 100)`
  * `P_ref::Float64`: （デフォルト: `1.0`）リファレンス負荷セットポイント（pu）、検証範囲: `(0, nothing)`
  * `ext::Dict{String, Any}`: （デフォルト: `Dict{String, Any}()`）シミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度。
  * `states::Vector{Symbol}`: (**変更しないでください。**) DEGOVモデルの[状態](@ref S)は：

```
x_ecb1: 電気制御ボックス 1,
x_ecb2: 電気制御ボックス 2,
x_a1: アクチュエーター 1,
x_a2: アクチュエーター 2,
x_a3: アクチュエーター 3,
```

  * `n_states::Int`: (**変更しないでください。**) DEGOVは5つの状態を持っています
  * `states_types::Vector{StateTypes}`: (**変更しないでください。**) DEGOVは5つの[微分](@ref states_list) [状態](@ref S)を持っています
  * `internal::InfrastructureSystemsInternal`: (**変更しないでください。**) PowerSystems.jl内部参照
