```
mutable struct SingleCageInductionMachine <: DynamicInjection
    name::String
    R_s::Float64
    R_r::Float64
    X_ls::Float64
    X_lr::Float64
    X_m::Float64
    H::Float64
    A::Float64
    B::Float64
    base_power::Float64
    ext::Dict{String, Any}
    C::Float64
    τ_ref::Float64
    B_shunt::Float64
    X_ad::Float64
    X_aq::Float64
    states::Vector{Symbol}
    n_states::Int
    internal::InfrastructureSystemsInternal
end
```

パラメータの5状態三相単一ケージ誘導機の二次トルク-速度関係

# 引数

  * `name::String`: コンポーネントの名前。同じタイプのコンポーネント（例：`PowerLoad`）はユニークな名前を持つ必要がありますが、異なるタイプのコンポーネント（例：`PowerLoad`と`ACBus`）は同じ名前を持つことができます。
  * `R_s::Float64`: アーマチュアスタター抵抗、検証範囲: `(0, nothing)`
  * `R_r::Float64`: ロータ抵抗、検証範囲: `(0, nothing)`
  * `X_ls::Float64`: スタータ漏れリアクタンス、検証範囲: `(0, nothing)`
  * `X_lr::Float64`: ロータ漏れリアクタンス、検証範囲: `(0, nothing)`
  * `X_m::Float64`: スタータ-ロータ相互リアクタンス、検証範囲: `(0, nothing)`
  * `H::Float64`: モーター慣性定数 [s]、検証範囲: `(0, nothing)`
  * `A::Float64`: トルク-速度二次項、検証範囲: `(0, 1)`
  * `B::Float64`: トルク-速度線形項、検証範囲: `(0, 1)`
  * `base_power::Float64`: ユニットの基準電力 (MVA) [単位化](@ref per_unit) のための、検証範囲: `(0, nothing)`
  * `ext::Dict{String, Any}`: (デフォルト: `Dict{String, Any}()`) シミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度。
  * `C::Float64`: (**変更しないでください。**) トルク-速度定数項
  * `τ_ref::Float64`: 参照トルクパラメータ
  * `B_shunt::Float64`: コンダクタンス初期化補正項
  * `X_ad::Float64`: (**変更しないでください。**) 等価d軸リアクタンス
  * `X_aq::Float64`: (**変更しないでください。**) 等価q軸リアクタンス
  * `states::Vector{Symbol}`: (**変更しないでください。**) [状態](@ref S) は：

```
ψ_qs: q軸のスタターフラックス、
ψ_ds: d軸のスタターフラックス、
ψ_qr: q軸のロータフラックス、
ψ_dr: d軸のロータフラックス、 
ωr: ロータ速度 [pu]、
```

  * `n_states::Int`: (**変更しないでください。**) SingleCageInductionMachineは5つの状態を持ちます
  * `internal::InfrastructureSystemsInternal`: (**変更しないでください。**) PowerSystems.jl内部参照
