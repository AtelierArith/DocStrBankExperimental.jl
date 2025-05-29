```
mutable struct SteamTurbineGov1 <: TurbineGov
    R::Float64
    T1::Float64
    valve_position_limits::MinMax
    T2::Float64
    T3::Float64
    D_T::Float64
    DB_h::Float64
    DB_l::Float64
    T_rate::Float64
    P_ref::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
    states_types::Vector{StateTypes}
    internal::InfrastructureSystemsInternal
end
```

蒸気タービン・ガバナー。このモデルは、PSS/EにおけるTGOV1またはTGOV1DUの両方を考慮します。

# 引数

  * `R::Float64`: ドループパラメータ、検証範囲: `(0, 0.1)`
  * `T1::Float64`: ガバナー時間定数、検証範囲: `(eps(), 0.5)`
  * `valve_position_limits::MinMax`: バルブ位置の制限
  * `T2::Float64`: リードラグリード時間定数、検証範囲: `(0, nothing)`
  * `T3::Float64`: リードラグラグ時間定数、検証範囲: `(eps(), 10)`
  * `D_T::Float64`: タービンダンピング、検証範囲: `(0, 0.5)`
  * `DB_h::Float64`: オーバースピードのデッドバンド、検証範囲: `(0, nothing)`
  * `DB_l::Float64`: アンダースピードのデッドバンド、検証範囲: `(nothing, 0)`
  * `T_rate::Float64`: タービンレート (MW)。ゼロの場合、発電機の基準が使用されます。検証範囲: `(0, nothing)`
  * `P_ref::Float64`: (デフォルト: `1.0`) 参照電力セットポイント (pu)、検証範囲: `(0, nothing)`
  * `ext::Dict{String, Any}`: (デフォルト: `Dict{String, Any}()`) シミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度など。
  * `states::Vector{Symbol}`: (**変更しないでください。**) SteamTurbineGov1モデルの[状態](@ref S)は次の通りです:

```
x_g1: バルブ開度,
x_g2: リードラグ状態
```

  * `n_states::Int`: (**変更しないでください。**) TGOV1は2つの状態を持ちます
  * `states_types::Vector{StateTypes}`: (**変更しないでください。**) TGOV1は2つの[differential](@ref states_list) [状態](@ref S)を持ちます
  * `internal::InfrastructureSystemsInternal`: (**変更しないでください。**) PowerSystems.jl内部参照
