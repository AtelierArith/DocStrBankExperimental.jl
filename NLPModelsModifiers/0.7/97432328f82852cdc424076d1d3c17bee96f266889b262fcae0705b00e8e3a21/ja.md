```
SpectralGradientModel(nlp; σ = 1.0)
```

別のタイプのnlpからHessianを`σI`として近似する`SpectralGradientModel`を構築します。キーワード引数`σ`は、単位行列の初期正の倍数です。使用されるアルゴリズムの詳細については、[`SpectralGradient operator documentation`](https://juliasmoothoptimizers.github.io/LinearOperators.jl/stable/reference/#LinearOperators.SpectralGradient)を参照してください。
