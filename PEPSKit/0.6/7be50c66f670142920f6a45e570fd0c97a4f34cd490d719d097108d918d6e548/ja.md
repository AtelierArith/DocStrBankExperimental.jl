```julia
struct SimultaneousCTMRG <: PEPSKit.CTMRGAlgorithm
```

CTMRGアルゴリズムは、すべての側面が同時に成長し、再正規化されるものです。特に、プロジェクターは2つの側面から同時にコーナーに適用されます。

## フィールド

  * `tol::Float64`
  * `maxiter::Int64`
  * `miniter::Int64`
  * `verbosity::Int64`
  * `projector_alg::PEPSKit.ProjectorAlgorithm`

## コンストラクタ

```
SimultaneousCTMRG(; kwargs...)
```

キーワード引数に基づいて同時CTMRGアルゴリズム構造体を構築します。完全な説明については、[`leading_boundary`](@ref)を参照してください。サポートされているキーワードは次のとおりです。

  * `tol::Real=1.0e-8`
  * `maxiter::Int=100`
  * `miniter::Int=4`
  * `verbosity::Int=2`
  * `trscheme::Union{TruncationScheme,NamedTuple}=(; alg::Symbol=:fixedspace)`
  * `svd_alg::Union{<:SVDAdjoint,NamedTuple}`
  * `projector_alg::Symbol=:halfinfinite`
