```
graph_cost(estimator::AbstractEstimator, graph::DAG)
```

グラフの総推定コストを取得します。コストのデータ型は実装によって選択できますが、使用可能な小なり比較演算子 (<)、基本的な数学演算子 (+, -)、および `zero()` と `typemax()` の実装を持っている必要があります。
