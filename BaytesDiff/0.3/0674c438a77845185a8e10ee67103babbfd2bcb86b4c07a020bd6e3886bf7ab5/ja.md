```julia
struct ℓDensityResult{T, S} <: BaytesDiff.ℓObjectiveResult
```

'ℓobjective' 評価のためのログ密度とパラメータの結果を 'parameter' に保存します。

# フィールド

  * `θᵤ::Any`: 制約のない空間でのパラメータ。
  * `ℓθᵤ::Any`: θᵤ におけるログ密度。
