```
fixpoint_reached(optimizer::AbstractOptimizer, graph::DAG)
```

フィックスポイントに到達できる最適化アルゴリズムによって実装される可能性のあるインターフェース関数で、到達したかどうかを `Bool` として返します。デフォルトの実装は `false` を返します。

関連情報: [`optimize_to_fixpoint!`](@ref)
