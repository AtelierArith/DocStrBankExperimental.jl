```julia
mutable struct NUTS{R<:BaytesDiff.ℓObjectiveResult, D<:BaytesDiff.AbstractDifferentiableTune, C<:BaytesMCMC.KineticEnergy} <: BaytesMCMC.MCMCKernel
```

NUTS - サンプリングプロセス全体で使用されるコンテナ。

# フィールド

  * `result::BaytesDiff.ℓObjectiveResult`: キャッシングのために保存されたターゲット結果。
  * `diff::BaytesDiff.AbstractDifferentiableTune`: 微分調整構造体。
  * `energy::BaytesMCMC.KineticEnergy`: ハミルトニアンに使用されるエネルギー。
  * `max_depth::Int64`: Uターンのための最大ツリー深度。
