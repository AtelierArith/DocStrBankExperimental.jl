```
mutable struct FixedDCSource <: DCSource
    voltage::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
    internal::InfrastructureSystemsInternal
end
```

固定DC電源のパラメータで、固定DC電圧を返します

# 引数

  * `voltage::Float64`: 電圧 (V)、検証範囲: `(0, nothing)`
  * `ext::Dict{String, Any}`: (デフォルト: `Dict{String, Any}()`) ユーザーがシミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度。
  * `states::Vector{Symbol}`: (**変更しないでください。**) FixedDCSourceには[states](@ref S)がありません
  * `n_states::Int`: (**変更しないでください。**) FixedDCSourceには状態がありません
  * `internal::InfrastructureSystemsInternal`: (**変更しないでください。**) PowerSystems.jl内部参照
