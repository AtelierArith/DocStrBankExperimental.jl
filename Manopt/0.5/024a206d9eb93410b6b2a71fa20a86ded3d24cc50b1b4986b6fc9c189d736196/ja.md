```
get_cost(M::AbstractManifold, sgo::ManifoldStochasticGradientObjective, p, i)
```

コストの `i` 番目の和項を評価します。

確率的コストに対して単一の関数を使用する場合、全体のコストを評価するために利用できるのはインデックス `i=1` のみです。
