```
mutable struct SalientPoleMachine <: Machine
    R::Float64
    Td0_p::Float64
    Td0_pp::Float64
    Tq0_pp::Float64
    Xd::Float64
    Xq::Float64
    Xd_p::Float64
    Xd_pp::Float64
    Xl::Float64
    Se::Tuple{Float64, Float64}
    ext::Dict{String, Any}
    γ_d1::Float64
    γ_q1::Float64
    γ_d2::Float64
    states::Vector{Symbol}
    n_states::Int
    internal::InfrastructureSystemsInternal
end
```

3-[states](@ref S)の顕著極同期機械のパラメータ、二次/指数飽和: IEEE Std 1110 §5.3.1 (モデル 2.1)。PSSEおよびPSLFのGENSALまたはGENSAEモデル

# 引数

  * `R::Float64`: アーマチュア抵抗、検証範囲: `(0, nothing)`
  * `Td0_p::Float64`: 瞬時d軸電圧の時間定数、検証範囲: `(0, nothing)`
  * `Td0_pp::Float64`: サブ瞬時d軸電圧の時間定数、検証範囲: `(0, nothing)`
  * `Tq0_pp::Float64`: サブ瞬時q軸電圧の時間定数、検証範囲: `(0, nothing)`
  * `Xd::Float64`: d軸のEMF後のリアクタンス（パー・ユニット）、検証範囲: `(0, nothing)`
  * `Xq::Float64`: q軸のEMF後のリアクタンス（パー・ユニット）、検証範囲: `(0, nothing)`
  * `Xd_p::Float64`: d軸のEMF後の瞬時リアクタンス（パー・ユニット）、検証範囲: `(0, nothing)`
  * `Xd_pp::Float64`: d軸のEMF後のサブ瞬時リアクタンス（パー・ユニット）。注意: Xd*pp = Xq*pp、検証範囲: `(0, nothing)`
  * `Xl::Float64`: ステータ漏れリアクタンス、検証範囲: `(0, nothing)`
  * `Se::Tuple{Float64, Float64}`: 1および1.2 puフラックスでの飽和係数: Se(eq*p) = B(eq*p-A)^2
  * `ext::Dict{String, Any}`: (デフォルト: `Dict{String, Any}()`) ユーザーがシミュレーションで使用されないメタデータ（緯度や経度など）を追加するための[*ext*ra辞書](@ref additional_fields)。
  * `γ_d1::Float64`: (**変更しないでください。**) γ_d1パラメータ
  * `γ_q1::Float64`: (**変更しないでください。**) γ_q1パラメータ
  * `γ_d2::Float64`: (**変更しないでください。**) γ_d2パラメータ
  * `states::Vector{Symbol}`: (**変更しないでください。**) [states](@ref S)は:

```
eq_p: 瞬時リアクタンスの背後にあるq軸発電機電圧、
ψ_kd: d軸の最初の等価減衰回路におけるフラックスリンク、
ψq_pp: q軸のサブ瞬時フラックスリンクの位相
```

  * `n_states::Int`: (**変更しないでください。**) SalientPoleMachineは3つの状態を持ちます
  * `internal::InfrastructureSystemsInternal`: (**変更しないでください。**) PowerSystems.jl内部参照
