```julia
struct ThermalInsulator
```

一般的な熱絶縁体。

  * `name::String`: 名前
  * `ρ::Float64`: 密度 [kg/m³]
  * `conductivity_coeffs::Vector{Float64}`: 温度の関数としての熱伝導率の係数 [W/(m⋅K)]
