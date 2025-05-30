```julia
struct SMC2Kernel{P<:BaytesFilters.ParticleFilter, M<:BaytesPMCMC.PMCMC} <: BaytesCore.AbstractAlgorithm
```

SMC2カーネルは、粒子の軌道のためのカーネルと、すべてのモデルパラメータのためのカーネルで構成されています。

# フィールド

  * `pf::BaytesFilters.ParticleFilter`: 時間にわたる（オンライン）状態伝播のためのカーネル。
  * `pmcmc::BaytesPMCMC.PMCMC`: ジッタリングステップのためのカーネル。
