```
ConstrainedBlackBoxContinuousSystem <: AbstractContinuousSystem
```

ドメイン制約のある右辺によって定義された連続時間システム：

$$
    x(t)' = f(x(t)), \; x(t) ∈ \mathcal{X} \; \forall t.
$$

### フィールド

  * `f`        – 右辺を保持する関数
  * `statedim` – 状態変数の数
  * `X`        – 状態制約
