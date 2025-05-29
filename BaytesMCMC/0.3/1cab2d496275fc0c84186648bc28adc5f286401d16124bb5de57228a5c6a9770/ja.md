```julia
mutable struct MALA{M<:BaytesDiff.ℓGradientResult, D<:BaytesDiff.AbstractDifferentiableTune} <: BaytesMCMC.MCMCKernel
```

MALAアルゴリズムコンテナ。

# フィールド

  * `result::BaytesDiff.ℓGradientResult`: 最後の伝播ステップのキャッシュされた結果。
  * `diff::BaytesDiff.AbstractDifferentiableTune`: 微分調整コンテナ
