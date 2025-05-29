```julia
struct PerturbedOracle{D, F, t, variance_reduction, G, R, S} <: InferOpt.AbstractOptimizationLayer
```

ブラックボックスオプティマイザのタイプ `F` の微分可能な摂動で、摂動のタイプ `D` を持ちます。

この構造体は、DifferentiableExpectations.jl の `Reinforce` のラッパーです。

パッケージ内で異なる動作をする3つの異なるコンストラクタがあります：

  * [`PerturbedOracle`](@ref)
  * [`PerturbedAdditive`](@ref)
  * [`PerturbedMultiplicative`](@ref)
