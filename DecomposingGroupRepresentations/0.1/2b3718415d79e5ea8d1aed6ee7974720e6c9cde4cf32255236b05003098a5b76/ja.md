```
struct DirectProductGroupAction <: AbstractGroupAction
```

ベクトル空間に対する直積群の作用を表します。

# 例

```jldoctest
julia> @polyvar x[1:3, 1:2];

julia> SO3 = LieGroup("SO", 3);

julia> a₁ = MatrixGroupAction(SO3, eachcol(x))
MatrixGroupAction of SO(3)
 2 ベクトルが作用下にあります: [x₁₋₁, x₂₋₁, x₃₋₁], [x₁₋₂, x₂₋₂, x₃₋₂]

julia> a₂ = ScalingLieGroupAction(x)
ScalingLieGroupAction of (ℂˣ)²
 ベクトルが作用下にあります: [x₁₋₁, x₂₋₁, x₃₋₁, x₁₋₂, x₂₋₂, x₃₋₂]
 作用:
  x₁₋₁ ↦ λ₁x₁₋₁, x₂₋₁ ↦ λ₁x₂₋₁, x₃₋₁ ↦ λ₁x₃₋₁
  x₁₋₂ ↦ λ₂x₁₋₂, x₂₋₂ ↦ λ₂x₂₋₂, x₃₋₂ ↦ λ₂x₃₋₂

julia> a₁ × a₂
DirectProductGroupAction of SO(3) × (ℂˣ)²
 リー作用:
```
