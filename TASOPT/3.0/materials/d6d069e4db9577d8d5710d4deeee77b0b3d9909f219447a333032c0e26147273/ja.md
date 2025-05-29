```julia
mutable struct StructuralAlloy
```

汎用構造合金。

  * `name::String`: 名前
  * `ρ::Float64`: 密度 [kg/m³]
  * `E::Float64`: ヤング率 [Pa]
  * `G::Float64`: 剪断弾性率 [Pa]
  * `ν::Float64`: ポアソン比 [-]
  * `σmax::Float64`: 最大応力（降伏または極限強度） [Pa]
  * `τmax::Float64`: 最大せん断 [Pa]
  * `YTS::Float64`: 降伏引張強度 [Pa]
  * `UTS::Float64`: 極限引張強度 [Pa]
  * `USS::Float64`: 極限せん断強度 [Pa]
  * `k::Float64`: 熱伝導率 [W/(m K)]
