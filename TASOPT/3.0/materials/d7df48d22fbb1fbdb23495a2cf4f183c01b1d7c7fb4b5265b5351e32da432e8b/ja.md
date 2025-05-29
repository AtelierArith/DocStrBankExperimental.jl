```julia
struct Conductor
```

一般的な導体。

  * `name::String`: 名前
  * `ρ::Float64`: 密度 [kg/m³]
  * `resistivity::Float64`: 抵抗率 [Ω⋅m]
  * `α::Float64`: 抵抗率の熱係数 [K⁻¹]
  * `T0::Float64`: 基準抵抗率での温度 [K]
