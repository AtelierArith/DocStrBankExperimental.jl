```
ScalingLieGroupAction <: AbstractGroupAction
```

スケーリングリー群の変数の集合に対する作用を表します。

# コンストラクタ

```julia
ScalingLieGroupAction(v::Vector{<:Variable})
ScalingLieGroupAction(V::AbstractMatrix{<:Variable})
ScalingLieGroupAction(G::ScalingLieGroup, v::Vector{<:Variable})
```

# 例

```jldoctest
julia> @polyvar x[1:2, 1:3];

julia> ScalingLieGroupAction(x)
ScalingLieGroupAction of (ℂˣ)³
 vector under action: [x₁₋₁, x₂₋₁, x₁₋₂, x₂₋₂, x₁₋₃, x₂₋₃]
 action:
  x₁₋₁ ↦ λ₁x₁₋₁, x₂₋₁ ↦ λ₁x₂₋₁
  x₁₋₂ ↦ λ₂x₁₋₂, x₂₋₂ ↦ λ₂x₂₋₂
  x₁₋₃ ↦ λ₃x₁₋₃, x₂₋₃ ↦ λ₃x₂₋₃

julia> ScalingLieGroupAction(x[:])
ScalingLieGroupAction of ℂˣ
 vector under action: [x₁₋₁, x₂₋₁, x₁₋₂, x₂₋₂, x₁₋₃, x₂₋₃]
 action:
  x₁₋₁ ↦ λx₁₋₁, x₂₋₁ ↦ λx₂₋₁, x₁₋₂ ↦ λx₁₋₂, x₂₋₂ ↦ λx₂₋₂, x₁₋₃ ↦ λx₁₋₃, x₂₋₃ ↦ λx₂₋₃
```
