```
BlackBoxDiscreteSystem <: AbstractDiscreteSystem
```

右辺が次の形で定義された離散時間システム：

$$
    x_{k+1} = f(x_k) \; \forall k.
$$

### フィールド

  * `f`        – 右辺を保持する関数
  * `statedim` – 状態変数の数
