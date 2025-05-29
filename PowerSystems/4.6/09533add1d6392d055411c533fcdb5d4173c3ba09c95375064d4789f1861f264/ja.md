```
mutable struct PSSFixed <: PSS
    V_pss::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
    internal::InfrastructureSystemsInternal
end
```

AVRの基準に加える固定電圧を返すPSSのパラメータ

# 引数

  * `V_pss::Float64`: puでの固定電圧安定化信号 ([`DEVICE_BASE`](@ref per_unit)), 検証範囲: `(0, nothing)`
  * `ext::Dict{String, Any}`: (デフォルト: `Dict{String, Any}()`) シミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度など。
  * `states::Vector{Symbol}`: (**変更しないでください。**) PSSFixedには[states](@ref S)がありません
  * `n_states::Int`: (**変更しないでください。**) PSSFixedには状態がありません
  * `internal::InfrastructureSystemsInternal`: (**変更しないでください。**) PowerSystems.jl内部参照
