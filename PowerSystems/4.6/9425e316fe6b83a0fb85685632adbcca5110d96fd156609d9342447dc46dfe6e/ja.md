```
mutable struct HydroTurbineGov <: TurbineGov
    R::Float64
    r::Float64
    Tr::Float64
    Tf::Float64
    Tg::Float64
    VELM::Float64
    gate_position_limits::MinMax
    Tw::Float64
    At::Float64
    D_T::Float64
    q_nl::Float64
    P_ref::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
    states_types::Vector{StateTypes}
    internal::InfrastructureSystemsInternal
end
```

水力タービン-ガバナー

# 引数

  * `R::Float64`: 永続的ドロップパラメータ、検証範囲: `(0, 0.1)`
  * `r::Float64`: 一時的ドロップ、検証範囲: `(0, 2)`
  * `Tr::Float64`: ガバナー時間定数、検証範囲: `(eps(), 30)`
  * `Tf::Float64`: フィルター時間定数、検証範囲: `(eps(), 0.1)`
  * `Tg::Float64`: サーボ時間定数、検証範囲: `(eps(), 1)`
  * `VELM::Float64`: ゲート速度制限、検証範囲: `(eps(), 0.3)`
  * `gate_position_limits::MinMax`: ゲート位置制限
  * `Tw::Float64`: 水時間定数、検証範囲: `(eps(), 3)`
  * `At::Float64`: タービンゲイン、検証範囲: `(0.8, 1.5)`
  * `D_T::Float64`: タービンダンピング、検証範囲: `(0, 0.5)`
  * `q_nl::Float64`: 無負荷流量、検証範囲: `(0, nothing)`
  * `P_ref::Float64`: (デフォルト: `1.0`) 参照電力セットポイント (pu)、検証範囲: `(0, nothing)`
  * `ext::Dict{String, Any}`: (デフォルト: `Dict{String, Any}()`) ユーザーがシミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度。
  * `states::Vector{Symbol}`: (**変更しないでください。**) HydroTurbineGovモデルの[状態](@ref S)は次の通りです:

```
x_g1: filter_output,
x_g2: desired gate, 
x_g3: gate opening, 
x_g4: turbine flow
```

  * `n_states::Int`: (**変更しないでください。**) HYGOVは4つの状態を持っています
  * `states_types::Vector{StateTypes}`: (**変更しないでください。**) HYGOVは4つの[微分](@ref states_list) [状態](@ref S)を持っています
  * `internal::InfrastructureSystemsInternal`: (**変更しないでください。**) PowerSystems.jl内部参照
