```
mutable struct AVRFixed <: AVR
    Vf::Float64
    V_ref::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
    states_types::Vector{StateTypes}
    internal::InfrastructureSystemsInternal
end
```

回転子巻線に固定電圧を返すAVRのパラメータ

# 引数

  * `Vf::Float64`: 回転子巻線に適用される固定電圧フィールド（pu）（[`DEVICE_BASE`](@ref per_unit)）、検証範囲: `(0, nothing)`
  * `V_ref::Float64`: （デフォルト: `1.0`）基準電圧セットポイント（pu）、検証範囲: `(0, nothing)`
  * `ext::Dict{String, Any}`: （デフォルト: `Dict{String, Any}()`）シミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度。
  * `states::Vector{Symbol}`: (**変更しないでください。**) 固定AVRには[状態](@ref S)がありません
  * `n_states::Int`: (**変更しないでください。**) 固定AVRには[状態](@ref S)がありません
  * `states_types::Vector{StateTypes}`: (**変更しないでください。**) 固定AVRには[状態](@ref S)がありません
  * `internal::InfrastructureSystemsInternal`: (**変更しないでください。**) PowerSystems.jl内部参照
