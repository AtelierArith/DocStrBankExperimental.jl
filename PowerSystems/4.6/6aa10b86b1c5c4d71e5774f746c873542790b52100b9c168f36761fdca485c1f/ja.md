```
mutable struct GasTG <: TurbineGov
    R::Float64
    T1::Float64
    T2::Float64
    T3::Float64
    AT::Float64
    Kt::Float64
    V_lim::Tuple{Float64, Float64}
    D_turb::Float64
    P_ref::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
    states_types::Vector{StateTypes}
    internal::InfrastructureSystemsInternal
end
```

ガスタービン-ガバナーのパラメータ。PSSEのGASTおよびPowerWorldのGAST_PTI

# 引数

  * `R::Float64`: スピードドロップパラメータ、検証範囲: `(eps(), 0.1)`
  * `T1::Float64`: ガバナーの時間定数（秒）、検証範囲: `(eps(), 0.5)`
  * `T2::Float64`: 燃焼室の時間定数、検証範囲: `(eps(), 0.5)`
  * `T3::Float64`: 負荷制限の時間定数（排気ガス測定時間）、検証範囲: `(eps(), 5)`
  * `AT::Float64`: 環境温度負荷制限、検証範囲: `(0, 1)`
  * `Kt::Float64`: 負荷制限フィードバックゲイン、検証範囲: `(0, 5)`
  * `V_lim::Tuple{Float64, Float64}`: 燃料バルブ開度の運用制御限界（V*min, V*max）
  * `D_turb::Float64`: ガスタービンローターのスピードダンピング係数、検証範囲: `(0, 0.5)`
  * `P_ref::Float64`: （デフォルト: `1.0`）基準負荷セットポイント（pu）、検証範囲: `(0, nothing)`
  * `ext::Dict{String, Any}`: （デフォルト: `Dict{String, Any}()`）シミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度。
  * `states::Vector{Symbol}`: (**変更しないでください。**) GASTモデルの[状態](@ref S)は次のとおりです：

```
x_g1: 燃料バルブ開度,
x_g2: 燃料流量,
x_g3: 排気温度負荷
```

  * `n_states::Int`: (**変更しないでください。**) GasTGは3つの状態を持ちます
  * `states_types::Vector{StateTypes}`: (**変更しないでください。**) GASTは3つの[微分](@ref states_list) [状態](@ref S)を持ちます
  * `internal::InfrastructureSystemsInternal`: (**変更しないでください。**) PowerSystems.jl内部参照
