```
VectorGradientFunction{E, FT, JT, F, J, I} <: AbstractManifoldObjective{E}
```

抽象ベクトル関数 $f:\mathcal M → ℝ^n$ を表し、（成分ごとに）勾配を提供します。[`AbstractEvaluationType`](@ref) `E` は評価タイプを示し、[`AbstractVectorialType`](@ref) の `FT` と `JT` は関数と勾配が提供される形式を示します。詳細については [`AbstractVectorFunction`](@ref) を参照してください。
