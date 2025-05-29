```
two_opt_neighborhood_search(::PermutationSolution, best_improvement)
```

2-opt近傍の体系的探索、すなわち部分列のすべての反転を考慮します。

近傍はランダム化された順序で探索されます。ブールパラメータbest_improvementは、最良改善または次の改善ステップ関数が使用されるかどうかを定義します。より良い解が見つかった場合はtrueを返します。
