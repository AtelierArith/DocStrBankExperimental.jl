```
struct IsotopeSource <: AbstractParticleSource
```

粒子源は、定義された崩壊系列に基づいて粒子を放出し、等方的、指向性の光線、または指向性の円錐放出のいずれかで動作します。

## フィールド

  * `Z::Int32`: 母核の原子番号。
  * `A::Int32`: 母核の質量数。
  * `ionCharge::Float64`: 母核の電荷。
  * `excitEnergy::Float64`: 母核の励起エネルギー。
  * `position::CartesianPoint`: ソースの位置。
  * `direction::CartesianVector`: ソースが粒子を放出する方向。
  * `opening_angle::AngleQuantity`: 指向性の円錐放出の場合の開口角。

## 例

```julia
# 方向が指定されていない場合の等方的放出
i1 = IsotopeSource(82, 212, 0, 0, CartesianPoint(0.04, 0, 0.05))
   
# 開口角が指定されていない場合の指向性光線放出
i2 = IsotopeSource(82, 212, 0, 0, CartesianPoint(0.04, 0, 0.05), CartesianVector(-1, 0, 0))

# 開口角が指定されている場合の指向性円錐放出
i3 = IsotopeSource(82, 212, 0, 0, CartesianPoint(0.04, 0, 0.05), CartesianVector(-1, 0, 0), 10u"°")
```

[`MonoenergeticSource`](@ref)も参照してください。
