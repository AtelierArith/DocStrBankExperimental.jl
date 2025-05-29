```
evaluate(nodes::AbstractVector{Node}, t0, t1[; batch_interval]) -> Vector{Block}
evaluate(node::Node, t0, t1[; batch_interval]) -> Block
```

指定されたノード（またはノード群）を指定された時間範囲 `[t0, t1)` にわたって評価し、対応する [`Block`](@ref)(s) を返します。

`nodes` に共通の依存関係がある場合、この評価を行う際に作業は繰り返されません。
