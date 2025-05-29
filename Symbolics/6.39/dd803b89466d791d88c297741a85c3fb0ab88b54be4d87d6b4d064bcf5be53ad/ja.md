```
SymbolicsSparsityDetector <: ADTypes.AbstractSparsityDetector
```

[Symbolics.jl トレーシングシステム](https://symbolics.juliasymbolics.org/stable/manual/sparsity_detection/)に基づくスパース性検出アルゴリズムです。

この型は、Symbolics.jlを[ADTypes.jl スパース性検出フレームワーク](https://sciml.github.io/ADTypes.jl/stable/#Sparsity-detector)と互換性を持たせます。以下の関数が実装されています：

  * `ADTypes.jacobian_sparsity` は [`Symbolics.jacobian_sparsity`](@ref) に基づいています
  * `ADTypes.hessian_sparsity` は [`Symbolics.hessian_sparsity`](@ref) に基づいています

# 参考文献

> [スパース性プログラミング：微分可能プログラミングにおける自動スパース性対応最適化](https://openreview.net/forum?id=rJlPdcY38B)、Gowda et al. (2019)

