```julia
struct DiagnosticsHMC{T<:AbstractFloat} <: BaytesMCMC.MCMCKernelDiagnostics
```

HMCサンプラーの診断フィールド。

# フィールド

  * `ϵ::AbstractFloat`: 離散化サイズ
  * `steps::Int64`: リープフロッグステップの数
