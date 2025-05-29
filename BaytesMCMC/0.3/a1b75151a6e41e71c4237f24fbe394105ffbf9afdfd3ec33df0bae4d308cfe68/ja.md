```julia
struct DiagnosticsMetropolis{T<:AbstractFloat} <: BaytesMCMC.MCMCKernelDiagnostics
```

メトロポリスサンプラーのデフォルト設定。

# フィールド

  * `ϵ::AbstractFloat`: 離散化サイズ
