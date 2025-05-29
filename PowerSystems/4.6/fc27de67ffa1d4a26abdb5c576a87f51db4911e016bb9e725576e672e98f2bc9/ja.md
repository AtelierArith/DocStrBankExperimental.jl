```
mutable struct PSSSimple <: PSS
    K_ω::Float64
    K_p::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
    internal::InfrastructureSystemsInternal
end
```

AVRの参照に加える比例ドロップ電圧を返すPSSのパラメータ

# 引数

  * `K_ω::Float64`: 周波数の比例ゲイン、検証範囲: `(0, nothing)`
  * `K_p::Float64`: 有効電力の比例ゲイン、検証範囲: `(0, nothing)`
  * `ext::Dict{String, Any}`: (デフォルト: `Dict{String, Any}()`) シミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度。
  * `states::Vector{Symbol}`: (**変更しないでください。**) PSSSimpleには[状態](@ref S)がありません
  * `n_states::Int`: (**変更しないでください。**) PSSSimpleには状態がありません
  * `internal::InfrastructureSystemsInternal`: (**変更しないでください。**) PowerSystems.jl内部参照
