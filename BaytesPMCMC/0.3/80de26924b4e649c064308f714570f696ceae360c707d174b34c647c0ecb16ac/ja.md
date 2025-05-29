```julia
struct PMCMC{M<:BaytesPMCMC.PMCMCKernel, N<:BaytesPMCMC.PMCMCTune} <: BaytesCore.AbstractAlgorithm
```

粒子MCMCコンテナ、コンテナカーネルおよびチューニング。

# フィールド

  * `kernel::BaytesPMCMC.PMCMCKernel`: PMCMCサンプラー
  * `tune::BaytesPMCMC.PMCMCTune`: カーネルのチューニング設定。
