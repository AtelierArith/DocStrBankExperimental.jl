```
ConstrainedBlackBoxControlContinuousSystem <: AbstractContinuousSystem
```

ドメイン制約のある右辺によって定義された連続時間制御システム：

$$
    x(t)' = f(x(t), u(t)), \; x(t) ∈ \mathcal{X}, \; u(t) ∈ \mathcal{U} \; \forall t.
$$

### フィールド

  * `f`        – 右辺を保持する関数
  * `statedim` – 状態変数の数
  * `inputdim` – 入力変数の数
  * `X`        – 状態制約
  * `U`        – 入力制約
