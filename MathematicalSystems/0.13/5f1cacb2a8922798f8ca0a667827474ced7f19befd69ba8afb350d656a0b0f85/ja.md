```
BlackBoxContinuousSystem <: AbstractContinuousSystem
```

右辺が次の形の連続時間システム:

$$
    x(t)' = f(x(t)) \; \forall t.
$$

### フィールド

  * `f`        – 右辺を保持する関数
  * `statedim` – 状態変数の数
