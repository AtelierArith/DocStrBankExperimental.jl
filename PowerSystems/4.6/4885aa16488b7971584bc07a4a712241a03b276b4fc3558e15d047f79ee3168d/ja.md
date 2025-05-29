```
mutable struct DynamicExponentialLoad <: DynamicInjection
    name::String
    a::Float64
    b::Float64
    α::Float64
    β::Float64
    T_p::Float64
    T_q::Float64
    ext::Dict{String, Any}
    base_power::Float64
    states::Vector{Symbol}
    n_states::Int
    internal::InfrastructureSystemsInternal
end
```

一般的な動的負荷モデルの2状態のパラメータは、["Voltage stability analysis using generic dynamic load models."](https://doi.org/10.1109/59.317575)に基づいています。

# 引数

  * `name::String`: コンポーネントの名前。同じタイプのコンポーネント（例：`PowerLoad`）はユニークな名前を持たなければなりませんが、異なるタイプのコンポーネント（例：`PowerLoad`と`ACBus`）は同じ名前を持つことができます。
  * `a::Float64`: 有効電力の静的指数係数、検証範囲: `(0, nothing)`
  * `b::Float64`: 無効電力の静的指数係数、検証範囲: `(0, nothing)`
  * `α::Float64`: 有効電力の過渡的指数係数、検証範囲: `(0, nothing)`
  * `β::Float64`: 無効電力の過渡的指数係数、検証範囲: `(0, nothing)`
  * `T_p::Float64`: 有効電力の時間定数、検証範囲: `(0, nothing)`
  * `T_q::Float64`: 無効電力の時間定数、検証範囲: `(0, nothing)`
  * `ext::Dict{String, Any}`: (デフォルト: `Dict{String, Any}()`) シミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度。
  * `base_power::Float64`: [パー・ユニット化](@ref per_unit)のための負荷の基準電力（MVA）
  * `states::Vector{Symbol}`: (**変更しないでください。**) [状態](@ref S)は：

```
x_p: 有効電力のインテグレータ状態、
x_q: 無効電力のインテグレータ状態、
```

  * `n_states::Int`: (**変更しないでください。**) DynamicExponentialLoadは2つの状態を持ちます。
  * `internal::InfrastructureSystemsInternal`: (**変更しないでください。**) PowerSystems.jl内部参照
