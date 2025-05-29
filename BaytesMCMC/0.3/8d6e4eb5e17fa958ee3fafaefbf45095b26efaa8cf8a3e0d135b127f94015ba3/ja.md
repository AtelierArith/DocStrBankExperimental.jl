```julia
struct MCMCDiagnostics{P, K<:BaytesMCMC.MCMCKernelDiagnostics, G, A} <: BaytesCore.AbstractDiagnostics
```

MCMC診断コンテナ。

# フィールド

  * `base::BaytesCore.BaseDiagnostics`: すべてのBaytesカーネルに使用される診断
  * `kernel::BaytesMCMC.MCMCKernelDiagnostics`: カーネル特有の診断。
  * `divergence::Bool`: 発散した場合のブール値。
  * `accept::BaytesCore.AcceptStatistic`: 現在のステップの受け入れ率。
  * `generated::Any`: 目的のために指定された生成量
  * `generated_algorithm::Any`: アルゴリズムのために指定された生成量
