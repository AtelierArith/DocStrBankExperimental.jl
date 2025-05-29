```
mutable struct FiveMassShaft <: Shaft
    H::Float64
    H_hp::Float64
    H_ip::Float64
    H_lp::Float64
    H_ex::Float64
    D::Float64
    D_hp::Float64
    D_ip::Float64
    D_lp::Float64
    D_ex::Float64
    D_12::Float64
    D_23::Float64
    D_34::Float64
    D_45::Float64
    K_hp::Float64
    K_ip::Float64
    K_lp::Float64
    K_ex::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
    internal::InfrastructureSystemsInternal
end
```

5質量スプリングシャフトモデルのパラメータ。高圧（HP）蒸気タービン、中圧（IP）蒸気タービン、低圧（LP）蒸気タービン、ローター、エキサイタ（EX）モーバーを含みます。

# 引数

  * `H::Float64`: ローター慣性定数（MWs/MVA）、検証範囲: `(0, nothing)`
  * `H_hp::Float64`: 高圧タービン慣性定数（MWs/MVA）、検証範囲: `(0, nothing)`
  * `H_ip::Float64`: 中圧タービン慣性定数（MWs/MVA）、検証範囲: `(0, nothing)`
  * `H_lp::Float64`: 低圧タービン慣性定数（MWs/MVA）、検証範囲: `(0, nothing)`
  * `H_ex::Float64`: エキサイタ慣性定数（MWs/MVA）、検証範囲: `(0, nothing)`
  * `D::Float64`: ローター自然減衰（pu）、検証範囲: `(0, nothing)`
  * `D_hp::Float64`: 高圧タービン自然減衰（pu）、検証範囲: `(0, nothing)`
  * `D_ip::Float64`: 中圧タービン自然減衰（pu）、検証範囲: `(0, nothing)`
  * `D_lp::Float64`: 低圧タービン自然減衰（pu）、検証範囲: `(0, nothing)`
  * `D_ex::Float64`: エキサイタ自然減衰（pu）、検証範囲: `(0, nothing)`
  * `D_12::Float64`: 高中圧タービン減衰、検証範囲: `(0, nothing)`
  * `D_23::Float64`: 中低圧タービン減衰、検証範囲: `(0, nothing)`
  * `D_34::Float64`: 低圧タービン-ローター減衰、検証範囲: `(0, nothing)`
  * `D_45::Float64`: ローター-エキサイタ減衰、検証範囲: `(0, nothing)`
  * `K_hp::Float64`: 高圧タービン角度係数、検証範囲: `(0, nothing)`
  * `K_ip::Float64`: 中圧タービン角度係数、検証範囲: `(0, nothing)`
  * `K_lp::Float64`: 低圧タービン角度係数、検証範囲: `(0, nothing)`
  * `K_ex::Float64`: エキサイタ角度係数、検証範囲: `(0, nothing)`
  * `ext::Dict{String, Any}`: (デフォルト: `Dict{String, Any}()`) ユーザーがシミュレーションで使用されないメタデータ（緯度や経度など）を追加するための[*ext*ra辞書](@ref additional_fields)。
  * `states::Vector{Symbol}`: (**変更しないでください。**) [状態](@ref S)は次のとおりです：

```
δ: ローター角度,
ω: ローター速度,
δ_hp: 高圧タービンのローター角度,
ω_hp: 高圧タービンのローター速度,
δ_ip: 中圧タービンのローター角度,
ω_ip: 中圧タービンのローター速度,
δ_lp: 低圧タービンのローター角度,
ω_lp: 低圧タービンのローター速度,
δ_ex: エキサイタのローター角度,
ω_lp: エキサイタのローター速度
```

  * `n_states::Int`: (**変更しないでください。**) FiveMassShaftは10の状態を持ちます。
  * `internal::InfrastructureSystemsInternal`: (**変更しないでください。**) PowerSystems.jl内部参照
