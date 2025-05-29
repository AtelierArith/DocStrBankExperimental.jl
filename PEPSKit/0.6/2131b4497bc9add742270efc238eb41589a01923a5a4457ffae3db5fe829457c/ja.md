```
struct SequentialCTMRG <: CTMRGAlgorithm
```

CTMRGアルゴリズムは、展開と再正規化が列ごとに順次行われます。これは、左に向かって成長し投影するステップの後に、時計回りの回転（4回実行される）として実装されています。

## フィールド

  * `tol::Float64`
  * `maxiter::Int64`
  * `miniter::Int64`
  * `verbosity::Int64`
  * `projector_alg::PEPSKit.ProjectorAlgorithm`

## コンストラクタ

```
SequentialCTMRG(; kwargs...)
```

キーワード引数に基づいて順次CTMRGアルゴリズム構造体を構築します。完全な説明については、[`leading_boundary`](@ref)を参照してください。サポートされているキーワードは次のとおりです。

  * `tol::Real=1.0e-8`
  * `maxiter::Int=100`
  * `miniter::Int=4`
  * `verbosity::Int=2`
  * `trscheme::Union{TruncationScheme,NamedTuple}=(; alg::Symbol=:fixedspace)`
  * `svd_alg::Union{<:SVDAdjoint,NamedTuple}`
  * `projector_alg::Symbol=:halfinfinite`
