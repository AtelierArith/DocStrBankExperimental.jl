```julia
struct PMCMCDiagnostics{T, P<:BaytesFilters.ParticleFilterDiagnostics, M<:BaytesMCMC.MCMCDiagnostics} <: BaytesCore.AbstractDiagnostics
```

対数尤度、期待サンプルサイズ、提案軌道に関する情報を含みます。

# フィールド

  * `base::BaytesCore.BaseDiagnostics`: すべてのBaytesカーネルに使用される診断
  * `pf::BaytesFilters.ParticleFilterDiagnostics`: パーティクルフィルタの診断。
  * `mcmc::BaytesMCMC.MCMCDiagnostics`: MCMCの診断。
