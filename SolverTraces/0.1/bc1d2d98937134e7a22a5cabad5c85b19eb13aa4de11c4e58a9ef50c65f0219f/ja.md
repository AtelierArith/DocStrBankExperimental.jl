```
SolverTrace(num_steps, i, print_interval, io, progress, columns, callbacks)
```

`num_steps` 回の反復に対するソルバートレースを表し、`i` は現在の反復を示します。[`next!`](@ref) が呼び出されるたびに、`i` は1ずつ増加し、`print_interval` の倍数に達すると、トレースに行が印刷されます。オプションで（デフォルト）、`ProgressMeter.Progress` も表示され、ソルバートレースの印刷間の進捗情報を提供します。
