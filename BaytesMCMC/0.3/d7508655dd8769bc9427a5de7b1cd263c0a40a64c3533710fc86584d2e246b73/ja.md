```julia
struct DiagnosticsCustom{T<:AbstractFloat} <: BaytesMCMC.MCMCKernelDiagnostics
```

カスタムサンプラーのデフォルト設定。

# フィールド

  * `ϵ::AbstractFloat`: 離散化サイズ
