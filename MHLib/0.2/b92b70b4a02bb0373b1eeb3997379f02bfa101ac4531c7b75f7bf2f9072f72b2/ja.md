```
k_flip_neighborhood_search!(::BoolVectorSolution, k::Int, best_improvement::Bool)
```

`k`フリップ局所探索の1回の主要な反復を実行します。つまり、1つの近傍を探索します。

`best_improvement`が設定されている場合、近傍は完全に探索され、最良の隣接解が保持されます。そうでない場合、探索は最初に見つかった改善解を保持する形で終了します。新しい双射値が返されます。
