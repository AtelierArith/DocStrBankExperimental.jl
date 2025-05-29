```
Solver(path_tracker; seed = nothing)
```

`path_tracker`の複数のコピーを含む構造体です。これは、[`solve`]を呼び出すために必要なすべての事前に割り当てられたデータ構造を含んでいます。`Solver`を構築する最も便利な方法は、[`solver_startsolutions`](@ref)を介することです。
