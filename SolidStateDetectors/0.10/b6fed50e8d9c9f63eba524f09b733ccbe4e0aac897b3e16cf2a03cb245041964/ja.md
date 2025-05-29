```
struct MonoenergeticSource <: AbstractParticleSource
```

モノエネルギー粒子を放出する粒子源で、等方的、指向性の光線、または指向性の円錐放出のいずれかです。

## フィールド

  * `particle_type::String`: ソースから放出される粒子の種類。
  * `energy::RealQuantity`: ソースから放出される粒子のエネルギー。
  * `position::CartesianPoint`: ソースの位置。
  * `direction::CartesianVector`: ソースが粒子を放出する方向。
  * `opening_angle::AngleQuantity`: 指向性の円錐放出の場合の開口角。

## 例

```julia
# 方向が指定されていない場合の等方的放出
m1 = MonoenergeticSource("gamma", 2.615u"MeV", CartesianPoint(0.04, 0, 0.05))

# 開口角が指定されていない場合の指向性光線放出
m2 = MonoenergeticSource("gamma", 2.615u"MeV", CartesianPoint(0.04, 0, 0.05), CartesianVector(-1, 0, 0))

# 開口角が指定されている場合の指向性円錐放出
m3 = MonoenergeticSource("gamma", 2.615u"MeV", CartesianPoint(0.04, 0, 0.05), CartesianVector(-1, 0, 0), 10u"°")
```

詳細は [`IsotopeSource`](@ref) を参照してください。
