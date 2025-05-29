```julia
mutable struct HMC{R<:BaytesDiff.ℓObjectiveResult, D<:BaytesDiff.AbstractDifferentiableTune, C<:BaytesMCMC.KineticEnergy, T<:BaytesCore.UpdateBool} <: BaytesMCMC.MCMCKernel
```

HMC - サンプリングプロセス全体で使用されるコンテナ。

# フィールド

  * `result::BaytesDiff.ℓObjectiveResult`: キャッシングのために保存されたターゲット結果。
  * `diff::BaytesDiff.AbstractDifferentiableTune`: 微分調整構造体。
  * `energy::BaytesMCMC.KineticEnergy`: ハミルトニアンに使用されるエネルギー。
  * `stepnumber::BaytesMCMC.StepNumberTune`: 離散化ステップのための調整構造体。
