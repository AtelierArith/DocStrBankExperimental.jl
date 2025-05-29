```
AdvectiveForcing(u=ZeroField(), v=ZeroField(), w=ZeroField())
```

速度場 `u, v, w` による輸送を表す強制項を構築し、輸送 `scheme` を指定します。

# 例

# トレーサーフィールドを使用して沈降粒子をモデル化する

```jldoctest
using Oceananigans

# 物理パラメータ
gravitational_acceleration          = 9.81     # m s⁻²
ocean_density                       = 1026     # kg m⁻³
mean_particle_density               = 2000     # kg m⁻³
mean_particle_radius                = 1e-3     # m
ocean_molecular_kinematic_viscosity = 1.05e-6  # m² s⁻¹

# 粘性流中の球の終端速度
Δb = gravitational_acceleration * (mean_particle_density - ocean_density) / ocean_density
ν = ocean_molecular_kinematic_viscosity
R = mean_particle_radius

w_Stokes = - 2/9 * Δb / ν * R^2 # m s⁻¹

settling = AdvectiveForcing(w=w_Stokes)

# 出力
AdvectiveForcing:
├── u: ZeroField{Int64}
├── v: ZeroField{Int64}
└── w: ConstantField(-1.97096)
```
