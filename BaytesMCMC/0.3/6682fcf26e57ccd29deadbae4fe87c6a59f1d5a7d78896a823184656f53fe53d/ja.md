```julia
mutable struct Custom{R<:BaytesDiff.ℓDensityResult, P} <: BaytesMCMC.MCMCKernel
```

カスタムアルゴリズムコンテナ。

# フィールド

  * `result::BaytesDiff.ℓDensityResult`: 最後の伝播ステップのキャッシュされた結果。
  * `proposal::Any`: 提案分布を返す `result.θᵤ` の呼び出し可能な構造体/クロージャ/関数。
