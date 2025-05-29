```julia
struct DiagnosticsMALA{T<:AbstractFloat} <: BaytesMCMC.MCMCKernelDiagnostics
```

MALAサンプラーの診断。

# フィールド

  * `ϵ::AbstractFloat`: 離散化サイズ
