```
mutable struct BaseMachine <: Machine
    R::Float64
    Xd_p::Float64
    eq_p::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
    internal::InfrastructureSystemsInternal
end
```

古典的な機械のパラメータ: PSSEおよびPSLFのGENCLS

# 引数

  * `R::Float64`: 機械の単位あたりのEMF後の抵抗、検証範囲: `(0, nothing)`
  * `Xd_p::Float64`: 機械の単位あたりのEMF後のリアクタンス、検証範囲: `(0, nothing)`
  * `eq_p::Float64`: インピーダンスの背後にある固定EMF、検証範囲: `(0, nothing)`
  * `ext::Dict{String, Any}`: (デフォルト: `Dict{String, Any}()`) シミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度。
  * `states::Vector{Symbol}`: (**変更しないでください。**) BaseMachineには[states](@ref S)がありません
  * `n_states::Int`: (**変更しないでください。**) BaseMachineには状態がありません
  * `internal::InfrastructureSystemsInternal`: (**変更しないでください。**) PowerSystems.jl内部参照
