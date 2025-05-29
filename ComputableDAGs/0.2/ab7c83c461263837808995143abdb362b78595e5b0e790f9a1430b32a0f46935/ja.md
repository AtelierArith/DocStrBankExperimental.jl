```
is_scheduled(graph::DAG)
```

グラフ全体がスケジュールされていることを検証します。すなわち、すべての [`ComputeTaskNode`](@ref) の `.device` が設定されていることを確認します。
