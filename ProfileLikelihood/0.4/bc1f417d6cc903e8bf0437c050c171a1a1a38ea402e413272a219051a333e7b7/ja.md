```
grid_search(prob::LikelihoodProblem, grid::AbstractGrid, parallel=Val(false); save_vals=Val(false))
```

与えられた `grid` と尤度問題 `prob` に対して、グリッドサーチを使用してグリッド上で最大化します。 `save_vals==Val(true)` の場合、各グリッドポイントでの尤度関数の値が返されます。マルチスレッドを希望する場合は、 `parallel=Val(true)` に設定してください。
