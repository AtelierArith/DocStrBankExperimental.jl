```julia
struct SemiMarkovTransition{A, B}
```

セミマルコフカーネルの状態と持続時間の遷移分布。

# フィールド

  * `state::Any`: 状態変数の遷移分布。
  * `duration::Any`: 持続時間変数の遷移分布。
