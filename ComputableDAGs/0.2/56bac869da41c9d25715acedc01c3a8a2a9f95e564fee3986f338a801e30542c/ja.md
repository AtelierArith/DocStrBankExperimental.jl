```
ReductionOptimizer
```

利用可能な [`NodeReduction`](@ref) を各ステップで単純に適用するオプティマイザです。 [`optimize_to_fixpoint!`](@ref) を実装しています。フィックスポイントは、グラフ内に可能な [`NodeReduction`](@ref) がもう存在しないときに達成されます。

関連情報: [`SplitOptimizer`](@ref)
