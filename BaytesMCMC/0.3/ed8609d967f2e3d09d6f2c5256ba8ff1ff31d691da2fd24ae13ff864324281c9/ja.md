```julia
mutable struct Metropolis{R<:BaytesDiff.ℓDensityResult} <: BaytesMCMC.MCMCKernel
```

メトロポリスアルゴリズムコンテナ。

# フィールド

  * `result::BaytesDiff.ℓDensityResult`: 最後の伝播ステップのキャッシュされた結果。
