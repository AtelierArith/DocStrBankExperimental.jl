```
SplitOptimizer
```

利用可能な [`NodeSplit`](@ref) を各ステップで単純に適用するオプティマイザーです。 [`optimize_to_fixpoint!`](@ref) を実装しています。フィックスポイントは、グラフ内に可能な [`NodeSplit`](@ref) がもう存在しないときに達成されます。

関連情報: [`ReductionOptimizer`](@ref)
