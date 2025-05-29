```
Scheduler(solution, methods, consider_initial_sol)
```

`MHMethod` スケジューラを作成します。

与えられた解に対して、与えられたメソッドを `Vector{MHMethod}` として提供するスケジューラを作成します。`consider_initial_sol` が `true` の場合、与えられた解を有効な初期解として考慮します。そうでない場合は、初期化されていないと見なされます。
