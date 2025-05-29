```julia
struct MCMC{M<:BaytesMCMC.MCMCKernel, N<:BaytesMCMC.MCMCTune} <: BaytesCore.AbstractAlgorithm
```

提案ステップの情報を格納します。

# フィールド

  * `kernel::BaytesMCMC.MCMCKernel`: MCMCサンプラー
  * `tune::BaytesMCMC.MCMCTune`: カーネルの調整設定。
