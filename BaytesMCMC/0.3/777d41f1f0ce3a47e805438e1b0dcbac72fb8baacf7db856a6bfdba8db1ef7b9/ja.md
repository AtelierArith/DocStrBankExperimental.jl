```julia
struct PhasePoint{T<:BaytesDiff.ℓObjectiveResult, S<:Real}
```

位相空間の点で、位置 BaytesDiff.ℓObjectiveResult と運動量 ρ で構成されています。

# フィールド

  * `result::BaytesDiff.ℓObjectiveResult`: BaytesDiff.ℓObjectiveResult コンテナ
  * `ρ::Vector{S} where S<:Real`: 運動量
