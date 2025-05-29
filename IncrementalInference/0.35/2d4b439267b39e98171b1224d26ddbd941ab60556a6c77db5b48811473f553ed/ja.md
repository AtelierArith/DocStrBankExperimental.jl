```julia
struct PartialPrior{T<:(IncrementalInference.SamplableBelief), P<:Tuple} <: DistributedFactorGraphs.AbstractPrior
```

任意の変数に対する部分事前信念（絶対データ）、`<:SamplableBelief` と意図した変数の次元を考慮して。

ノート

  * [`AMP.ManifoldKernelDensity`](@ref) を使用する場合、部分を二重にしないでください。この `PartialPrior` コンテナ内でのみ部分を定義してください。

      * 将来的に未定、より一般的な抽象化のために `AMP.getManifoldPartial` を使用することを検討してください。
