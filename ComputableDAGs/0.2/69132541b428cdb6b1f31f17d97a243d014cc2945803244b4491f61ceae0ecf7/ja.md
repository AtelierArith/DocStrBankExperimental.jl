```
optimize_to_fixpoint!(optimizer::AbstractOptimizer, graph::DAG)
```

固定点に到達できる最適化アルゴリズムによって実装される可能性のあるインターフェース関数です。アルゴリズムは、その固定点に到達するまで実行され、その時点で [`fixpoint_reached`](@ref) は true を返すべきです。

通常の実装は次のようになります：

```julia
    function optimize_to_fixpoint!(optimizer::MyOptimizer, graph::DAG)
        while !fixpoint_reached(optimizer, graph)
            optimize_step!(optimizer, graph)
        end
        return nothing
    end
```
