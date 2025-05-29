```julia
struct ParticleGibbs{P<:BaytesFilters.ParticleFilter, M<:BaytesMCMC.MCMC} <: BaytesPMCMC.PMCMCKernel
```

PMCMCコンストラクタのデフォルト引数。

# フィールド

  * `pf::BaytesFilters.ParticleFilter`: 潜在軌道を推定するための粒子フィルタカーネル。
  * `mcmc::BaytesMCMC.MCMC`: 連続モデルパラメータをサンプリングするためのMCMCカーネル。
