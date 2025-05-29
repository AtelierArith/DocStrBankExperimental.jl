```
mutable struct SauerPaiMachine <: Machine
    R::Float64
    Xd::Float64
    Xq::Float64
    Xd_p::Float64
    Xq_p::Float64
    Xd_pp::Float64
    Xq_pp::Float64
    Xl::Float64
    Td0_p::Float64
    Tq0_p::Float64
    Td0_pp::Float64
    Tq0_pp::Float64
    ext::Dict{String, Any}
    γ_d1::Float64
    γ_q1::Float64
    γ_d2::Float64
    γ_q2::Float64
    states::Vector{Symbol}
    n_states::Int
    internal::InfrastructureSystemsInternal
end
```

同期機のパラメータ: Sauer Pai モデル

# 引数

  * `R::Float64`: 機械のEMF後の抵抗（単位）、検証範囲: `(0, nothing)`
  * `Xd::Float64`: d軸のEMF後のリアクタンス（単位）、検証範囲: `(0, nothing)`
  * `Xq::Float64`: q軸のEMF後のリアクタンス（単位）、検証範囲: `(0, nothing)`
  * `Xd_p::Float64`: d軸のEMF後の過渡リアクタンス（単位）、検証範囲: `(0, nothing)`
  * `Xq_p::Float64`: q軸のEMF後の過渡リアクタンス（単位）、検証範囲: `(0, nothing)`
  * `Xd_pp::Float64`: d軸のEMF後のサブ過渡リアクタンス（単位）、検証範囲: `(0, nothing)`
  * `Xq_pp::Float64`: q軸のEMF後のサブ過渡リアクタンス（単位）、検証範囲: `(0, nothing)`
  * `Xl::Float64`: ステータ漏れリアクタンス、検証範囲: `(0, nothing)`
  * `Td0_p::Float64`: 過渡d軸電圧の時間定数、検証範囲: `(0, nothing)`
  * `Tq0_p::Float64`: 過渡q軸電圧の時間定数、検証範囲: `(0, nothing)`
  * `Td0_pp::Float64`: サブ過渡d軸電圧の時間定数、検証範囲: `(0, nothing)`
  * `Tq0_pp::Float64`: サブ過渡q軸電圧の時間定数、検証範囲: `(0, nothing)`
  * `ext::Dict{String, Any}`: (デフォルト: `Dict{String, Any}()`) ユーザーがシミュレーションで使用されないメタデータ（緯度や経度など）を追加するための[*ext*ra辞書](@ref additional_fields)。
  * `γ_d1::Float64`: (**変更しないでください。**) 内部方程式
  * `γ_q1::Float64`: (**変更しないでください。**) 内部方程式
  * `γ_d2::Float64`: (**変更しないでください。**) 内部方程式
  * `γ_q2::Float64`: (**変更しないでください。**) 内部方程式
  * `states::Vector{Symbol}`: (**変更しないでください。**) [状態](@ref S) は:

```
ψq: q軸ステータフラックス,
ψd: d軸ステータフラックス,
eq_p: q軸過渡電圧,
ed_p: d軸過渡電圧
ψd_pp: d軸のサブ過渡フラックス結合
ψq_pp: q軸のサブ過渡フラックス結合
```

  * `n_states::Int`: (**変更しないでください。**) SauerPaiMachine は 6 つの状態を持ちます
  * `internal::InfrastructureSystemsInternal`: (**変更しないでください。**) PowerSystems.jl 内部参照
