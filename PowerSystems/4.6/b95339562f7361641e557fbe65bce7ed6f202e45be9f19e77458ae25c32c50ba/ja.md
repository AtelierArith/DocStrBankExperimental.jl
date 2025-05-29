```
mutable struct AVRSimple <: AVR
    Kv::Float64
    V_ref::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
    states_types::Vector{StateTypes}
    internal::InfrastructureSystemsInternal
end
```

EMFの導関数における単純比例AVRのパラメータ、すなわちEMFに対するインテグレータ制御器

# 引数

  * `Kv::Float64`: 比例ゲイン、検証範囲: `(0, nothing)`
  * `V_ref::Float64`: (デフォルト: `1.0`) 参照電圧セットポイント (pu)、検証範囲: `(0, nothing)`
  * `ext::Dict{String, Any}`: (デフォルト: `Dict{String, Any}()`) ユーザーがシミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度。
  * `states::Vector{Symbol}`: (**変更しないでください。**) [状態](@ref S)は次の通りです:

```
Vf: フィールド電圧
```

  * `n_states::Int`: (**変更しないでください。**) 固定AVRは1つの[状態](@ref S)を持ちます
  * `states_types::Vector{StateTypes}`: (**変更しないでください。**) 単純AVRは1つの[微分](@ref states_list) [状態](@ref S)を持ちます
  * `internal::InfrastructureSystemsInternal`: (**変更しないでください。**) PowerSystems.jl内部参照
