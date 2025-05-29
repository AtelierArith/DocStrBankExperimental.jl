```julia
struct PEPSOptimize{G}
```

ADを使用したPEPS基底状態最適化のためのアルゴリズム構造体。詳細については[`fixedpoint`](@ref)を参照してください。

## フィールド

  * `boundary_alg::PEPSKit.CTMRGAlgorithm`
  * `gradient_alg::Any`
  * `optimizer_alg::OptimKit.OptimizationAlgorithm`
  * `reuse_env::Bool`
  * `symmetrization::Union{Nothing, PEPSKit.SymmetrizationStyle}`

## コンストラクタ

```
PEPSOptimize(; kwargs...)
```

キーワード引数に基づいてPEPS最適化アルゴリズム構造体を構築します。完全な説明については[`fixedpoint`](@ref)を参照してください。サポートされているキーワードは次のとおりです。

  * `boundary_alg::Union{NamedTuple,<:CTMRGAlgorithm}`
  * `gradient_alg::Union{NamedTuple,Nothing,<:GradMode}`
  * `optimizer_alg::Union{NamedTuple,<:OptimKit.OptimizationAlgorithm}`
  * `reuse_env::Bool=true`
  * `symmetrization::Union{Nothing,SymmetrizationStyle}=nothing`
