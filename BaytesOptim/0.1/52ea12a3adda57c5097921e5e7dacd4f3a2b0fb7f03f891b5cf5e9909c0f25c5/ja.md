```julia
mutable struct CustomAlgorithm{R<:BaytesDiff.ℓDensityResult, T<:BaytesOptim.CustomAlgorithmTune} <: BaytesCore.AbstractAlgorithm
```

提案ステップの情報を格納します。

# フィールド

  * `result::BaytesDiff.ℓDensityResult`
  * `tune::BaytesOptim.CustomAlgorithmTune`
