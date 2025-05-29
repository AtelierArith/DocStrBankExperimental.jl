```
mutable struct TGFixed <: TurbineGov
    efficiency::Float64
    P_ref::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
    internal::InfrastructureSystemsInternal
end
```

固定タービンガバナーのパラメータで、P_ref*efficiencyの積によって与えられる固定機械トルクを返します。

# 引数

  * `efficiency::Float64`: `P_ref`に掛け算される効率係数、検証範囲: `(0, nothing)`
  * `P_ref::Float64`: (デフォルト: `1.0`) 参照電力セットポイント (pu)、検証範囲: `(0, nothing)`
  * `ext::Dict{String, Any}`: (デフォルト: `Dict{String, Any}()`) シミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度。
  * `states::Vector{Symbol}`: (**変更しないでください。**) TGFixedには[states](@ref S)がありません。
  * `n_states::Int`: (**変更しないでください。**) TGFixedには状態がありません。
  * `internal::InfrastructureSystemsInternal`: (**変更しないでください。**) PowerSystems.jl内部参照。
