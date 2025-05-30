```
ConstrainedAffineControlContinuousSystem
```

ドメイン制約を持つ連続時間アフィン制御システムの形式：

$$
    x(t)' = A x(t) + B u(t) + c, \; x(t) ∈ \mathcal{X}, \; u(t) ∈ \mathcal{U} \; \forall t.
$$

### フィールド

  * `A` – 状態行列
  * `B` – 入力行列
  * `c` – アフィン項
  * `X` – 状態制約
  * `U` – 入力制約
