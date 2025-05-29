```julia
struct SemiMarkovInitiation{A, B}
```

半マルコフカーネルの状態と持続時間の初期分布。

# フィールド

  * `state::Any`: 状態変数の初期分布。
  * `duration::Any`: 持続時間変数の初期分布。
