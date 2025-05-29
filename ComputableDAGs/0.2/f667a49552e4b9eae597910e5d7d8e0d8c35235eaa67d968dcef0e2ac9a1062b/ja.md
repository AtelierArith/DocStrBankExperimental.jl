```
operation_effect(estimator::AbstractEstimator, graph::DAG, operation::Operation)
```

グラフのコストに対する推定効果を取得します。すなわち、`graph_cost(estimator, graph) + operation_effect(estimator, graph, operation) ~= graph_cost(estimator, graph_with_operation_applied)` です。これは厳密な要件ではありませんが、推定が良いほど最適化アルゴリズムは良くなります。

!!! note
    この関数のデフォルト実装があり、操作を適用し、[`graph_cost`](@ref) を呼び出し、その後再び操作をポップします。

    特定の推定器に対してこの関数をオーバーロードし、可能であれば操作から効果を直接計算する方がはるかに高速です。

