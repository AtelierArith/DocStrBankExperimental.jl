```julia
struct DiagnosticsNUTS{T<:AbstractFloat} <: BaytesMCMC.MCMCKernelDiagnostics
```

NUTSサンプラーの診断フィールド。

# フィールド

  * `ℓH::AbstractFloat`: 対数密度（負のエネルギー）。
  * `depth::Int64`: ツリーの深さ。
  * `termination::BaytesMCMC.InvalidTree`: 終了理由。[`InvalidTree`](@ref)および[`REACHED_MAX_DEPTH`](@ref)を参照してください。
  * `acceptance_rate::AbstractFloat`: 受け入れ率統計。
  * `ϵ::AbstractFloat`: 離散化サイズ
  * `steps::Int64`: 評価されたリープフロッグステップの数。
  * `directions::BaytesMCMC.Directions`: ツリーの倍増のための方向（デバッグに便利）。
