```
mutable struct SingleMass <: Shaft
    H::Float64
    D::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
    internal::InfrastructureSystemsInternal
end
```

単一質量シャフトモデルのパラメータ。通常はロータ質量を表します。

# 引数

  * `H::Float64`: ロータ慣性定数（MWs/MVA）、検証範囲: `(0, nothing)`
  * `D::Float64`: ロータ自然減衰（pu）、検証範囲: `(0, nothing)`
  * `ext::Dict{String, Any}`: (デフォルト: `Dict{String, Any}()`) シミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度。
  * `states::Vector{Symbol}`: (**変更しないでください。**) [状態](@ref S)は：

```
δ: ロータ角度,
ω: ロータ速度
```

  * `n_states::Int`: (**変更しないでください。**) SingleMassは1つの状態を持ちます。
  * `internal::InfrastructureSystemsInternal`: (**変更しないでください。**) PowerSystems.jl内部参照。
