```
mutable struct RoundRotorMachine <: Machine
    R::Float64
    Td0_p::Float64
    Td0_pp::Float64
    Tq0_p::Float64
    Tq0_pp::Float64
    Xd::Float64
    Xq::Float64
    Xd_p::Float64
    Xq_p::Float64
    Xd_pp::Float64
    Xl::Float64
    Se::Tuple{Float64, Float64}
    ext::Dict{String, Any}
    γ_d1::Float64
    γ_q1::Float64
    γ_d2::Float64
    γ_q2::Float64
    γ_qd::Float64
    states::Vector{Symbol}
    n_states::Int
    internal::InfrastructureSystemsInternal
end
```

4-[states](@ref S) のラウンドロータ同期機械のパラメータ（2次/指数飽和）：IEEE Std 1110 §5.3.2 (モデル 2.2)。PSSEおよびPSLFにおけるGENROUまたはGENROEモデル

# 引数

  * `R::Float64`: アーマチュア抵抗、検証範囲: `(0, nothing)`
  * `Td0_p::Float64`: 過渡d軸電圧の時間定数、検証範囲: `(0, nothing)`
  * `Td0_pp::Float64`: サブ過渡d軸電圧の時間定数、検証範囲: `(0, nothing)`
  * `Tq0_p::Float64`: 過渡q軸電圧の時間定数、検証範囲: `(0, nothing)`
  * `Tq0_pp::Float64`: サブ過渡q軸電圧の時間定数、検証範囲: `(0, nothing)`
  * `Xd::Float64`: d軸のEMF後のリアクタンス（パー・ユニット）、検証範囲: `(0, nothing)`
  * `Xq::Float64`: q軸のEMF後のリアクタンス（パー・ユニット）、検証範囲: `(0, nothing)`
  * `Xd_p::Float64`: d軸のEMF後の過渡リアクタンス（パー・ユニット）、検証範囲: `(0, nothing)`
  * `Xq_p::Float64`: q軸のEMF後の過渡リアクタンス（パー・ユニット）、検証範囲: `(0, nothing)`
  * `Xd_pp::Float64`: d軸のEMF後のサブ過渡リアクタンス（パー・ユニット）。注意: Xd*pp = Xq*pp、検証範囲: `(0, nothing)`
  * `Xl::Float64`: ステータ漏れリアクタンス、検証範囲: `(0, nothing)`
  * `Se::Tuple{Float64, Float64}`: 1および1.2 puフラックスでの飽和係数: S(1.0) = B(|ψ_pp|-A)^2
  * `ext::Dict{String, Any}`: (デフォルト: `Dict{String, Any}()`) シミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例: 緯度と経度。
  * `γ_d1::Float64`: (**変更しないでください。**) γ_d1パラメータ
  * `γ_q1::Float64`: (**変更しないでください。**) γ_q1パラメータ
  * `γ_d2::Float64`: (**変更しないでください。**) γ_d2パラメータ
  * `γ_q2::Float64`: (**変更しないでください。**) γ_q2パラメータ
  * `γ_qd::Float64`: (**変更しないでください。**) γ_qdパラメータ
  * `states::Vector{Symbol}`: (**変更しないでください。**) [states](@ref S) は：

```
eq_p: 過渡リアクタンスの背後にあるq軸発電機電圧、
ed_p: 過渡リアクタンスの背後にあるd軸発電機電圧、
ψ_kd: d軸の最初の等価減衰回路におけるフラックス結合、
ψ_kq: d軸の最初の等価減衰回路におけるフラックス結合
```

  * `n_states::Int`: (**変更しないでください。**) RoundRotorMachineは4つの状態を持ちます
  * `internal::InfrastructureSystemsInternal`: (**変更しないでください。**) PowerSystems.jl内部参照
