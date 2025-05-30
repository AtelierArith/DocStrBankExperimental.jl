```
BlackBoxControlContinuousSystem <: AbstractContinuousSystem
```

右辺が次の形で定義された連続時間制御システム:

$$
    x(t)' = f(x(t), u(t)) \; \forall t.
$$

### フィールド

  * `f`        – 右辺を保持する関数
  * `statedim` – 状態変数の数
  * `inputdim` – 入力変数の数
